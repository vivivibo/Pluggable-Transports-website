---
layout: single
title: Meet the Transports
permalink: /transports/

excerpt: ""
header:
  overlay_image: /assets/images/SunsetTrainTracksCrop_Arne Hückelheim_notify_wikimedia.JPG
  caption: "Photo credit: [**© Arne Hückelheim**](https://en.wikipedia.org/wiki/User:Knipptang)"
#  cta_label: "More Info"
#  cta_url: "https://unsplash.com"

sidebar:
    nav: "aboutnav"
---
There are many different transports which address a wide variety of blocking strategies. At a very high-level standpoint, they can be grouped into three strategies: Diverting, Scrambling and Shapeshifting.

{% include toc icon="file-text" %}

## Diverting

In this case, traffic is moved around the network using different paths to standard web traffic. One way of diverting traffic is known as "domain fronting". This approach leverages cloud platforms which are socially or economically difficult to block - it pushes traffic through a "front", which is commonly an IP address shared by many sites on the cloud provider. To effectively block an app using domain fronting requires blocking the entire cloud provider -- and every other service hosted by it. This approach has been less successful in the past couple of years, due to large cloud providers removing the ability to front using their services.

Another way of diverting traffic is to use bridges that can be easily brought up and connected through for a short period of time. Once these devices are discovered, the app is able to find new bridges and connect through them. This kind of approach requires a lot of devices to act as bridges, and for apps to have the intelligence to discover new bridges.

## Scrambling

This approach seeks to disguise the traffic in ways that are not identifiable as any specific type of traffic. This forces an adversary to only allowed whitelisted traffic (which can be easily defeated by fronting) or to expend significant resources to re-identify the scrambled traffic. Scrambling tends to work best where there is not only a willingness to outright block large platform providers, but also to take part in DPI analysis of internet traffic.

Scrambling relies on having clients being able to know or discover unblocked IP addresses, and an active censor will work to discover and block these addresses. Once a server address is known it is no longer usable.

## Shapeshifting

"Shapeshifting" hide the traffic in non-objectional formats, making it look like a VOIP call, web traffic, online games, or statistically sampled "normal" traffic. This approach defeats whitelisted traffic limitations, but is almost impossible to do "perfectly" -- even if the traffic is indistinguishable from "real" traffic, the client and server will generally behave differently from a "real" server - meaning that advanced adversaries can choose to expend resources to do follow-up scans on every suspected connection to verify the server acts "correctly," and block it if not.

## Current Implementations

| **Transport** | **Information** | **Strategy** |
|----|-------|
|**[meek](https://trac.torproject.org/projects/tor/wiki/doc/meek)** | For a long time, Meek was considered the gold standard as it supported domain fronting through Google App Engine, Amazon Web Services and Microsoft Azure. It is now used much less frequently, and only when allowed by the cloud provider. | Diverting (domain fronting) |
|**[SnowFlake](https://keroserene.net/snowflake/)** | SnowFlake uses WebRTC to turn website visitors into ephemeral proxies. See also [torproject.org/projects/tor/wiki/doc/Snowflake](https://trac.torproject.org/projects/tor/wiki/doc/Snowflake). As Snowflake use increases, more Snowflake bridges will need to be built and disoverability of these bridges will be the key to its success. | Diverting |
|**[Refraction Networking](https://refraction.network/)** | This approach involves intercepting traffic at the ISP or network operator level, and redirecting traffic from perceived "safe" addresses to user-requested, blocked content. It increases the cost of censorship, by preventing censors from selectively blocking only those servers used to provide Internet freedom. | Diverting |
|**[obfs4](https://github.com/Yawning/obfs4)**| Obfs4 is the current state of the art deployed "look-like nothing" obfuscation protocol from The Tor Project. It evolved from [obfs2](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/tree/doc/obfs2/obfs2-protocol-spec.txt) and [obfs3](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/tree/doc/obfs3/obfs3-protocol-spec.txt) to include active probing defences, and is in wide use today. Tor have published and unpublished bridges, increasing the effort needed by the adversary to block them. | Scrambling |
|**[Dust2](https://github.com/blanu/Dust)**|Dust transforms traffic to statistically match a pattern of "allowed" traffic | Shapeshifting |
| **[Stegotorus](https://github.com/TheTorProject/stegotorus)**| [Stegotorus](https://github.com/TheTorProject/stegotorus) A development framework that provides an API specifically geared towards the needs of steganographic protocols. With this API, developers can help applications hide from DPI, and to resist throttling or connection dropping. | Shapeshifting |
|**[Lampshade](https://github.com/getlantern/lampshade)**| An obfuscated encrypted network protocol for [Lantern](https://getlantern.org) | Shapeshifting |
|**[Optimizer](link)**| A pluggable transport that works with other transports to find the best option by making use of multiple configurable strategies to find the optimal choice among the available transports. | Various |
|**[Replicant](https://github.com/OperatorFoundation/shapeshifter-transports/tree/main/transports/Replicant/v2)**| An "adversary-tunable" transport that can be adapted to provide the obfuscation needed by any specific adversary. | Shapeshifting |

Now that you know what transports are available, let's look at how to [make sure they're working](/measuring).

<p style="text-align:left;"><a href="/how-transports/">&lt; Previous</a>
<span style="float:right;"><a href="/measuring/">Next &gt;</a></span>
</p>

