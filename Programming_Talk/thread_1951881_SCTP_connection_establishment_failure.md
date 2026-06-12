---
title: "SCTP connection establishment failure"
date: 2012-04-03
forum: Programming Talk
---

### Post by swanaku on 2012-04-03
Hi,

When Server and Client applications are running on the single linux machine, SCTP connection establishment is failing. Both server and client virtual IPs are defined in the machine.
 
Wireshark logs show the below signalling sequence:
INIT     ----->
ABORT     <-----     ( From kernel)
INIT_ACK <-----     ( From Server )

The ABORT is resulting in the connection establishment failure.
Here are the kernel debug statements:
Mar 28 10:58:38 server kernel: sctp_init_sock(sk: ffff81031a6bda80)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 11)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 2)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 1)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 0)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 1)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 2)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 3)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 8)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 9)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 11)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 13)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 0)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 1)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 3)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 2)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 13)
Mar 28 10:58:38 server kernel: sctp_bind(sk: ffff81031a6bda80, addr: ffff810654ca1ec8, addr_len: 16)
Mar 28 10:58:38 server kernel: sctp_do_bind(sk: ffff81031a6bda80, new addr: 10.196.4.22, port: 0, new port: 35199, len: 16)
Mar 28 10:58:38 server kernel: sctp_get_port() begins, snum=35199
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 0)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 1)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 3)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 2)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 13)
Mar 28 10:58:38 server kernel: sctp_setsockopt(sk: ffff81031a6bda80... optname: 11)
Mar 28 10:58:38 server kernel: sctp_connect - sk: ffff81031a6bda80, sockaddr: ffff810654ca1ec8, addr_len: 16
Mar 28 10:58:38 server kernel: Created asoc ffff8103107ec000
Mar 28 10:58:38 server kernel: sctp_assoc_add_peer:association ffff8103107ec000 addr: 10.196.4.18 port: 32199 state:UNKNOWN
Mar 28 10:58:38 server kernel: sctp_v4_get_dst: DST:10.196.4.18, SRC:0.0.0.0 - <7>rt_dst:10.196.4.18, rt_src:10.196.4.18
Mar 28 10:58:38 server kernel: sctp_assoc_add_peer:association ffff8103107ec000 PMTU set to 16436
Mar 28 10:58:38 server kernel: sctp_packet_init: packet:ffff810353a67950 transport:ffff810353a67800
Mar 28 10:58:38 server kernel: sctp_do_sm prefn: ep ffff810353a67400, EVENT_T_PRIMITIVE, PRIMITIVE_ASSOCIATE, asoc 
ffff8103107ec000[STATE_CLOSED], sctp_sf_do_prm_asoc
Mar 28 10:58:38 server kernel: sctp_do_sm postfn: asoc ffff8103107ec000, status: DISPOSITION_CONSUME
Mar 28 10:58:38 server kernel: sctp_cmd_new_state: asoc ffff8103107ec000[STATE_COOKIE_WAIT]
Mar 28 10:58:38 server kernel: sctp_assoc_update_retran_path:association ffff8103107ec000 addr: 10.196.4.18 port: 32199
Mar 28 10:58:38 server kernel: sctp_outq_tail(ffff8103107ed5b0, ffff81031a69bec0[INIT])
Mar 28 10:58:38 server kernel: sctp_packet_config: packet:ffff810353a67950 vtag:0x0
Mar 28 10:58:38 server kernel: sctp_packet_init: packet:ffff810654ca1ba8 transport:ffff810353a67800
Mar 28 10:58:38 server kernel: sctp_packet_config: packet:ffff810654ca1ba8 vtag:0x0
Mar 28 10:58:38 server kernel: sctp_packet_append_chunk: packet:ffff810654ca1ba8 chunk:ffff81031a69bec0
Mar 28 10:58:38 server kernel: sctp_packet_transmit: packet:ffff810654ca1ba8
Mar 28 10:58:38 server kernel: ***sctp_transmit_packet***
Mar 28 10:58:38 server kernel: *** Chunk ffff81031a69bec0[INIT] No TSN 0x0, length 44, chunk->skb->len 44, rtt_in_progress 0
Mar 28 10:58:38 server kernel: sctp_v4_get_dst: DST:10.196.4.18, SRC:0.0.0.0 - <7>rt_dst:10.196.4.18, rt_src:10.196.4.22
Mar 28 10:58:38 server kernel: sctp_assoc_sync_pmtu: asoc:ffff8103107ec000, pmtu:16436, frag_point:1416
Mar 28 10:58:38 server kernel: ***sctp_transmit_packet*** skb len 56
Mar 28 10:58:38 server kernel: sctp_v4_xmit: skb:ffff81033dd1d480, len:56, src:10.196.4.22, dst:10.196.4.18
Mar 28 10:58:38 server kernel: +++sctp_inq_pop+++ chunk ffff81031a69bec0[INIT], length 44, skb->len 40
Mar 28 10:58:38 server kernel: sctp_do_sm prefn: ep ffff81066ef5b800, EVENT_T_CHUNK, INIT, asoc 0000000000000000[STATE_CLOSED], 
sctp_sf_do_5_1B_init
Mar 28 10:58:38 server kernel: sctp_v4_get_dst: DST:10.196.4.22, SRC:10.196.4.18 - <7>rt_dst:10.196.4.22, rt_src:10.196.4.18
Mar 28 10:58:38 server kernel: sctp_packet_init: packet:ffff810353409d50 transport:ffff810353409c00
Mar 28 10:58:38 server kernel: sctp_packet_config: packet:ffff810353409d50 vtag:0x30d77e59
Mar 28 10:58:38 server kernel: chunkifying skb ffff81033dd1d280 w/o an sk
Mar 28 10:58:38 server kernel: sctp_packet_append_chunk: packet:ffff810353409d50 chunk:ffff81031a69bdc0
Mar 28 10:58:38 server kernel: sctp_do_sm postfn: asoc 0000000000000000, status: DISPOSITION_CONSUME
Mar 28 10:58:38 server kernel: sctp_packet_transmit: packet:ffff810353409d50
Mar 28 10:58:38 server kernel: ***sctp_transmit_packet***
Mar 28 10:58:38 server kernel: *** Chunk ffff81031a69bdc0[ABORT] No TSN 0x0, length 4, chunk->skb->len 4, rtt_in_progress 0
Mar 28 10:58:38 server kernel: ***sctp_transmit_packet*** skb len 16
Mar 28 10:58:38 server kernel: sctp_v4_xmit: skb:ffff81033dd1d680, len:16, src:10.196.4.18, dst:10.196.4.22
Mar 28 10:58:38 server kernel: sctp_packet_free: packet:ffff810353409d50
Mar 28 10:58:38 server kernel: sctp_do_sm post sfx: error 0, asoc 0000000000000000[STATE_CLOSED]
Mar 28 10:58:38 server kernel: sctp_do_sm post sfx: error 0, asoc ffff8103107ec000[STATE_CLOSED]
Mar 28 10:58:38 server kernel: sctp_wait_for_connect: asoc=ffff8103107ec000, timeo=9223372036854775807
Mar 28 10:58:38 server kernel: +++sctp_inq_pop+++ chunk ffff81031a69bec0[ABORT], length 4, skb->len 0
Mar 28 10:58:38 server kernel: sctp_do_sm prefn: ep ffff810353a67400, EVENT_T_CHUNK, ABORT, asoc ffff8103107ec000[STATE_COOKIE_WAIT], 
sctp_sf_cookie_wait_abort
Mar 28 10:58:38 server kernel: ABORT received (INIT).
Mar 28 10:58:38 server kernel: sctp_do_sm postfn: asoc ffff8103107ec000, status: DISPOSITION_ABORT
Mar 28 10:58:38 server kernel: sctp_cmd_new_state: asoc ffff8103107ec000[STATE_CLOSED]
Mar 28 10:58:38 server kernel: sm_sideff: event_up: ffff81033dd428d8, ulpq: ffff8103107ed618.
Mar 28 10:58:38 server kernel: sctp_cmd_new_state: asoc ffff8103107ec000[STATE_CLOSED]
Mar 28 10:58:38 server kernel: sctp_packet_free: packet:ffff810353a67950
Mar 28 10:58:38 server kernel: sctp_do_sm post sfx: error 0, asoc ffff8103107ec000[STATE_CLOSED]
Mar 28 10:58:38 server kernel: About to exit __sctp_connect() free asoc: 0000000000000000 kaddrs: ffff810654ca1ec8 err: -111
Mar 28 10:58:38 server kernel: +++sctp_inq_pop+++ chunk ffff81031163de80[INIT_ACK], length 128, skb->len 124
Mar 28 10:58:38 server kernel: sctp_do_sm prefn: ep ffff81066ef5b800, EVENT_T_CHUNK, INIT_ACK, asoc 0000000000000000[STATE_CLOSED], 
sctp_sf_discard_chunk
Mar 28 10:58:38 server kernel: Chunk 2 is discarded
Mar 28 10:58:38 server kernel: sctp_do_sm postfn: asoc 0000000000000000, status: DISPOSITION_DISCARD
Mar 28 10:58:38 server kernel: Ignored sctp protocol event - state 1, event_type 1, event_id 2
Mar 28 10:58:38 server kernel: sctp_do_sm post sfx: error 0, asoc 0000000000000000[STATE_CLOSED]
Mar 28 10:58:38 server kernel: sctp_close(sk: 0xffff81031a6bda80, timeout:0)
Mar 28 10:58:38 server kernel: sctp_destroy_sock(sk: ffff81031a6bda80)

And, when Server and Client applications are running on different Linux servers , the problem is not observed.
 
Can some one suggest us what could be the problem for the connection failure and any work around to resolve the issue?

Thanks !!!
 
Regards,
Swapna.

---

