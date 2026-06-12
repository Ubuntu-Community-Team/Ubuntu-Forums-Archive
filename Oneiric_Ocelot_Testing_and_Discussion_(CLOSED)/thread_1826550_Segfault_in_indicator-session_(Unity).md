---
title: "Segfault in indicator-session (Unity)"
date: 2011-08-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lidex on 2011-08-16
Has anyone seen this issue?
On desktop loading or running from terminal:
```
'/usr/lib/indicator-session/indicator-session-service' 
```
I get this output in dmesg:
```
dmesg | tail -30
[   24.295766] indicator-sessi[1483]: segfault at 0 ip 00007f64138e9230 sp 00007fffcd485a68 error 4 in libglib-2.0.so.0.2916.0[7f6413884000+f5000]
[   25.383284] indicator-sessi[1490]: segfault at 0 ip 00007fbc29d29230 sp 00007fff45e008b8 error 4 in libglib-2.0.so.0.2916.0[7fbc29cc4000+f5000]
[   27.261981] indicator-sessi[1499]: segfault at 0 ip 00007fb78a8d0230 sp 00007fffe9b71438 error 4 in libglib-2.0.so.0.2916.0[7fb78a86b000+f5000]
[   29.980012] eth0: no IPv6 routers present
[   30.742013] indicator-sessi[1507]: segfault at 0 ip 00007f0895cf3230 sp 00007fff6ced1b98 error 4 in libglib-2.0.so.0.2916.0[7f0895c8e000+f5000]
[   37.426004] indicator-sessi[1514]: segfault at 0 ip 00007f25e07ad230 sp 00007fffabe9e3d8 error 4 in libglib-2.0.so.0.2916.0[7f25e0748000+f5000]
[   50.501618] indicator-sessi[1521]: segfault at 0 ip 00007fa3cd3ca230 sp 00007fff482d7bf8 error 4 in libglib-2.0.so.0.2916.0[7fa3cd365000+f5000]
[   65.825833] compiz[1627]: segfault at 58 ip 000000000043c4d0 sp 00007fffd2e7c6c8 error 4 in compiz[400000+6f000]
[   74.062840] indicator-sessi[1794]: segfault at 0 ip 00007fcf92dc7230 sp 00007fff0c4bef58 error 4 in libglib-2.0.so.0.2916.0[7fcf92d62000+f5000]
[   74.587763] indicator-sessi[1822]: segfault at 0 ip 00007fc544812230 sp 00007fff68a337b8 error 4 in libglib-2.0.so.0.2916.0[7fc5447ad000+f5000]
[   75.364447] indicator-sessi[1835]: segfault at 0 ip 00007faf8cbc2230 sp 00007fff7824d528 error 4 in libglib-2.0.so.0.2916.0[7faf8cb5d000+f5000]
[   76.146455] indicator-sessi[1846]: segfault at 0 ip 00007fb870a03230 sp 00007fff87f17bb8 error 4 in libglib-2.0.so.0.2916.0[7fb87099e000+f5000]
[   77.278813] indicator-sessi[1864]: segfault at 0 ip 00007fe9272e3230 sp 00007fff41650e28 error 4 in libglib-2.0.so.0.2916.0[7fe92727e000+f5000]
[   79.179217] indicator-sessi[1871]: segfault at 0 ip 00007f7c96b62230 sp 00007fff8f95cc18 error 4 in libglib-2.0.so.0.2916.0[7f7c96afd000+f5000]
[   82.799881] indicator-sessi[1878]: segfault at 0 ip 00007f1aadf41230 sp 00007fffb663d308 error 4 in libglib-2.0.so.0.2916.0[7f1aadedc000+f5000]
[   89.725762] indicator-sessi[1890]: segfault at 0 ip 00007fa782c0c230 sp 00007fff3fe30b18 error 4 in libglib-2.0.so.0.2916.0[7fa782ba7000+f5000]
[  102.963207] indicator-sessi[1902]: segfault at 0 ip 00007f8a56af3230 sp 00007fffaf60f7e8 error 4 in libglib-2.0.so.0.2916.0[7f8a56a8e000+f5000]
[  129.030865] indicator-sessi[1965]: segfault at 0 ip 00007fccee016230 sp 00007fff964d66d8 error 4 in libglib-2.0.so.0.2916.0[7fccedfb1000+f5000]
[  180.666157] indicator-sessi[1979]: segfault at 0 ip 00007fca49ee5230 sp 00007fff9da278c8 error 4 in libglib-2.0.so.0.2916.0[7fca49e80000+f5000]
[  283.471632] indicator-sessi[2101]: segfault at 0 ip 00007fc0b5772230 sp 00007fff7071bdb8 error 4 in libglib-2.0.so.0.2916.0[7fc0b570d000+f5000]
[  488.726664] indicator-sessi[2135]: segfault at 0 ip 00007f7a5e872230 sp 00007fff58877578 error 4 in libglib-2.0.so.0.2916.0[7f7a5e80d000+f5000]
[  898.715863] indicator-sessi[2240]: segfault at 0 ip 00007f5acd9ea230 sp 00007fff55de8e48 error 4 in libglib-2.0.so.0.2916.0[7f5acd985000+f5000]
[ 1707.225972] indicator-sessi[2869]: segfault at 0 ip 00007f38fc048230 sp 00007fffc19846e8 error 4 in libglib-2.0.so.0.2916.0[7f38fbfe3000+f5000]
[ 1718.305977] indicator-sessi[2889]: segfault at 0 ip 00007fb9d990b230 sp 00007fff05345b68 error 4 in libglib-2.0.so.0.2916.0[7fb9d98a6000+f5000]
[ 1743.792989] indicator-sessi[2897]: segfault at 0 ip 00007f81e5ed2230 sp 00007fff19ebb498 error 4 in libglib-2.0.so.0.2916.0[7f81e5e6d000+f5000]
[ 1786.501379] indicator-sessi[2908]: segfault at 0 ip 00007f982c8a4230 sp 00007fff2a2c4568 error 4 in libglib-2.0.so.0.2916.0[7f982c83f000+f5000]
[ 2184.392762] indicator-sessi[2923]: segfault at 0 ip 00007f77e3972230 sp 00007fffcabd4b38 error 4 in libglib-2.0.so.0.2916.0[7f77e390d000+f5000]
[ 3319.285433] indicator-sessi[3523]: segfault at 0 ip 00007eff60d6b230 sp 00007fff43fbbe08 error 4 in libglib-2.0.so.0.2916.0[7eff60d06000+f5000]
[ 3357.066138] indicator-sessi[3534]: segfault at 0 ip 00007f79b5c0d230 sp 00007fffb5fa9e18 error 4 in libglib-2.0.so.0.2916.0[7f79b5ba8000+f5000]
[ 4421.357887] indicator-sessi[4275]: segfault at 0 ip 00007f3d1ba00230 sp 00007fff0698f418 error 4 in libglib-2.0.so.0.2916.0[7f3d1b99b000+f5000]

```
I have an icon in the unity panel, but no functionality. Another oddity is the lightdm screen is missing a section right where the indicators would appear and the time shows there. ???

---

### Post by lidex on 2011-08-18
Bug report here:
[https://bugs.launchpad.net/indicator-session/+bug/824243](https://bugs.launchpad.net/indicator-session/+bug/824243)

---

