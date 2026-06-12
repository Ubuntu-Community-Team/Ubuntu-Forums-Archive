---
title: "[JAVA] i2p and Eclipse"
date: 2007-10-27
forum: Programming Talk
---

### Post by Mathiasdm on 2007-10-27
I'm going to post my message from the i2p forums, since I (sadly) don't get a reply. Perhaps my question is too stupid? I hope somebody can help me with this.

I'd like to try to program a bit for i2p.
Sadly, I'm not that experienced, and I seem to have a few problems...
I used Eclipse (and the CVS option in Eclipse) to get i2p, but Eclipse seems to report TONS of errors (over 28000 !).

I'm guessing I forgot about dependencies or something. I'm afraid I can't seem to find a lot of documentation on the i2p website.

I'll post the first few errors (100), perhaps you guys can tell me what I did wrong  :oops: 

Oh, and I'm using Ubuntu Gutsy Gibbon, in case that matters.

```

Severity and Description	Path	Resource	Location	Creation Time	Id
__template__ cannot be resolved	i2p/apps/q/java/src/HTML	Template.java	line 407	1193312517662	46762
__template__ cannot be resolved	i2p/apps/q/java/src/HTML	Template.java	line 882	1193312517663	46808
__template__ cannot be resolved	i2p/apps/q/java/src/HTML	Template.java	line 905	1193312517663	46812
__template__ cannot be resolved	i2p/apps/q/java/src/HTML	Template.java	line 922	1193312517664	46815
__template__ cannot be resolved	i2p/apps/q/java/src/HTML	Template.java	line 946	1193312517664	46818
__template__ cannot be resolved	i2p/apps/q/java/src/HTML	Template.java	line 983	1193312517664	46822
_actualPeer cannot be resolved	i2p/router/java/src/net/i2p/router/transport/tcp	ConnectionBuilder.java	line 138	1193312520518	53882
_actualPeer cannot be resolved	i2p/router/java/src/net/i2p/router/transport/tcp	ConnectionBuilder.java	line 789	1193312520519	53946
_actualPeer cannot be resolved	i2p/router/java/src/net/i2p/router/transport/tcp	ConnectionHandler.java	line 167	1193312511074	28969
_actualPeer cannot be resolved	i2p/router/java/src/net/i2p/router/transport/tcp	ConnectionHandler.java	line 675	1193312511078	29021
_actualPeer cannot be resolved	i2p/router/java/src/net/i2p/router/transport/tcp	ConnectionHandler.java	line 701	1193312511078	29022
_adminManager cannot be resolved	i2p/router/java/src/net/i2p/router	RouterContext.java	line 96	1193312512290	31415
_AESEngine cannot be resolved	i2p/core/java/src/net/i2p	I2PAppContext.java	line 311	1193312518676	48165
_AESEngine cannot be resolved	i2p/core/java/src/net/i2p	I2PAppContext.java	line 315	1193312518676	48166
_alreadyChanged cannot be resolved	i2p/router/java/src/net/i2p/router	RouterClock.java	line 43	1193312515229	38517
_alreadyChanged cannot be resolved	i2p/router/java/src/net/i2p/router	RouterClock.java	line 53	1193312515229	38526
_alreadyChanged cannot be resolved	i2p/router/java/src/net/i2p/router	RouterClock.java	line 86	1193312515230	38531
_alreadyChanged cannot be resolved	i2p/router/java/src/net/i2p/router	RouterClock.java	line 99	1193312515230	38546
_archive cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	FilteredThreadIndex.java	line 27	1193312515875	41632
_archive cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	FilteredThreadIndex.java	line 28	1193312515875	41633
_archive cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 67	1193312517815	47172
_archive cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 118	1193312517815	47191
_archive cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	HTMLRenderer.java	line 131	1193312515481	39685
_archive cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	ThreadedHTMLRenderer.java	line 498	1193312519528	52229
_archive cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	ThreadedHTMLRenderer.java	line 507	1193312519528	52235
_attachments cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	CachedEntry.java	line 28	1193312519581	52552
_attachments cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	CachedEntry.java	line 46	1193312519581	52560
_attachments cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	CachedEntry.java	line 97	1193312519581	52572
_attachments cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	CachedEntry.java	line 111	1193312519581	52576
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 41	1193312515988	42203
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 42	1193312515988	42205
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 52	1193312515989	42214
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 58	1193312515989	42220
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 59	1193312515989	42222
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 63	1193312515989	42224
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 64	1193312515989	42225
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 65	1193312515989	42227
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 67	1193312515989	42230
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 69	1193312515989	42233
_authSignature cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelVerificationStructure.java	line 81	1193312515989	42241
_bandwidthLimiter cannot be resolved	i2p/router/java/src/net/i2p/router	RouterContext.java	line 123	1193312512290	31427
_bandwidthLimiter cannot be resolved	i2p/router/java/src/net/i2p/router	RouterContext.java	line 294	1193312512290	31458
_base cannot be resolved	i2p/router/java/src/net/i2p/router/networkdb/kademlia	XORComparator.java	line 17	1193312513038	34272
_base cannot be resolved	i2p/router/java/src/net/i2p/router/networkdb/kademlia	XORComparator.java	line 23	1193312513038	34277
_base cannot be resolved	i2p/router/java/src/net/i2p/router/networkdb/kademlia	XORComparator.java	line 24	1193312513038	34280
_bindings cannot be resolved	i2p/installer/lib/launch4j/src/net/sf/launch4j/formimpl	ConfigFormImpl.java	line 59	1193312519328	51373
_bindings cannot be resolved	i2p/installer/lib/launch4j/src/net/sf/launch4j/formimpl	ConfigFormImpl.java	line 119	1193312519329	51412
_bindings cannot be resolved	i2p/installer/lib/launch4j/src/net/sf/launch4j/formimpl	ConfigFormImpl.java	line 131	1193312519329	51415
_blockCache cannot be resolved	i2p/router/java/src/net/i2p/router/transport/udp	PacketBuilder.java	line 190	1193312513823	34745
_blockCache cannot be resolved	i2p/router/java/src/net/i2p/router/transport/udp	PacketBuilder.java	line 193	1193312513823	34747
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	CachedEntry.java	line 32	1193312519581	52554
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	CachedEntry.java	line 37	1193312519581	52556
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	CachedEntry.java	line 81	1193312519581	52568
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	User.java	line 83	1193312512279	31338
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	User.java	line 108	1193312512279	31342
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	User.java	line 110	1193312512279	31343
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	User.java	line 111	1193312512279	31345
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie	User.java	line 212	1193312512280	31367
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 22	1193312517814	47158
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 145	1193312517815	47199
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 163	1193312517815	47208
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 192	1193312517815	47223
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 202	1193312517816	47229
_blog cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/sml	BlogRenderer.java	line 222	1193312517816	47233
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 25	1193312518915	49606
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 38	1193312518915	49609
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 50	1193312518915	49612
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 62	1193312518915	49615
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 62	1193312518915	49616
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 65	1193312518915	49618
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 76	1193312518915	49621
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 82	1193312518915	49623
_blogHash cannot be resolved	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 83	1193312518915	49624
_blogHash cannot be resolved or is not a field	i2p/apps/syndie/java/src/net/i2p/syndie/data	BlogURI.java	line 76	1193312518915	49622
_browser cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	I2PTunnelHTTPServer.java	line 143	1193312518686	48224
_browser cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	I2PTunnelHTTPServer.java	line 159	1193312518686	48231
_browser cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	I2PTunnelHTTPServer.java	line 163	1193312518686	48234
_buf cannot be resolved	i2p/core/java/src/net/i2p/util	CachingByteArrayOutputStream.java	line 22	1193312515736	41065
_buf cannot be resolved	i2p/core/java/src/net/i2p/util	CachingByteArrayOutputStream.java	line 23	1193312515736	41067
_buf cannot be resolved	i2p/core/java/src/net/i2p/util	CachingByteArrayOutputStream.java	line 26	1193312515736	41068
_buildMessageHandlerJob cannot be resolved	i2p/router/java/src/net/i2p/router/tunnel/pool	BuildHandler.java	line 62	1193312520399	52963
_buildReplyMessageHandlerJob cannot be resolved	i2p/router/java/src/net/i2p/router/tunnel/pool	BuildHandler.java	line 63	1193312520399	52964
_cache cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	HTTPResponseOutputStream.java	line 50	1193312517191	44166
_cache cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	HTTPResponseOutputStream.java	line 51	1193312517191	44169
_cache cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	HTTPResponseOutputStream.java	line 101	1193312517191	44183
_cache cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	HTTPResponseOutputStream.java	line 192	1193312517191	44206
_cache cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	I2PTunnelRunner.java	line 239	1193312514182	36561
_cache cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	I2PTunnelRunner.java	line 257	1193312514183	36571
_cache cannot be resolved	i2p/apps/i2ptunnel/java/src/net/i2p/i2ptunnel	I2PTunnelRunner.java	line 308	1193312514183	36585
_cache cannot be resolved	i2p/apps/sam/java/src/net/i2p/sam	SAMStreamSession.java	line 573	1193312520804	55583
_cache cannot be resolved	i2p/apps/sam/java/src/net/i2p/sam	SAMStreamSession.java	line 591	1193312520804	55590
_cache cannot be resolved	i2p/apps/sam/java/src/net/i2p/sam	SAMStreamSession.java	line 670	1193312520805	55602
_cache cannot be resolved	i2p/apps/streaming/java/src/net/i2p/client/streaming	MessageInputStream.java	line 73	1193312520873	56051
_cache cannot be resolved	i2p/apps/streaming/java/src/net/i2p/client/streaming	PacketQueue.java	line 63	1193312512985	34018
_cache cannot be resolved	i2p/apps/streaming/java/src/net/i2p/client/streaming	PacketQueue.java	line 106	1193312512986	34038
_cache cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelDataMessage.java	line 86	1193312512350	31973
_cache cannot be resolved	i2p/router/java/src/net/i2p/data/i2np	TunnelDataMessage.java	line 108	1193312512350	31979
_cache cannot be resolved	i2p/router/java/src/net/i2p/router/transport/udp	MessageReceiver.java	line 37	1193312519335	51438
_cache cannot be resolved	i2p/router/java/src/net/i2p/router/transport/udp	MessageReceiver.java	line 89	1193312519335	51458
_cache cannot be resolved	i2p/router/java/src/net/i2p/router/transport/udp	MessageReceiver.java	line 141	1193312519335	51469

```

---

### Post by Mathiasdm on 2007-10-28
Sorry about bumping this to the top,but  I can't seem to solve the problem :-( By the way, the CVS of i2p is located at [http://www.i2p.net/cvs](http://www.i2p.net/cvs) .

Interesting to note, Eclipse seems to say (for several packages) things like:
"The declared package 'net.i2p.router.tunnel' does not match the expected package 'router.java.test.net.i2p.router.tunnel'".

Help would be appreciated!

---

