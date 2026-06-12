---
title: "Ubuntu 14.04 LTS server and UDPXY"
date: 2016-03-17
forum: New to Ubuntu
---

### Post by dejan-ciric-do on 2016-03-17
I need to multicast stream which comes on eth1 to forward on eth0 so  other computers and students in subnet can see it(connecting mcast  stream to router or switch for everyone just mess with network and  bandwidth and stream is freezing and pixeling ), (in what ever manner,  but best will be as http stream so students can open stream with VLC)  First I need to verify that stream is available, and for that I try with  Ubuntu desktop and its working with one NIC, but with two no. After to  much time without solution I decide to move to server 14.04 and UDPXY.  Now I Installed Ubuntu server 14.04, server is joined multicast group,  with tcpdump -i I can see that mcast stream is here on eth1, can't open  the stream because it's server without video card, I installed UDPXY,  which is accepting mcast stream on eth1 and client requests on eth0 so  they open stream like: [http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)    I try to open stream in VLC on Windows, and on Linux computer and  nothing. The VLC log gives me the same massage like before on Ubuntu  desktop.

---

### Post by sandyd on 2016-03-17
> **dejan-ciric-do said:**
> I need to multicast stream which comes on eth1 to forward on eth0 so  other computers and students in subnet can see it(connecting mcast  stream to router or switch for everyone just mess with network and  bandwidth and stream is freezing and pixeling ), (in what ever manner,  but best will be as http stream so students can open stream with VLC)  First I need to verify that stream is available, and for that I try with  Ubuntu desktop and its working with one NIC, but with two no. After to  much time without solution I decide to move to server 14.04 and UDPXY.  Now I Installed Ubuntu server 14.04, server is joined multicast group,  with tcpdump -i I can see that mcast stream is here on eth1, can't open  the stream because it's server without video card, I installed UDPXY,  which is accepting mcast stream on eth1 and client requests on eth0 so  they open stream like: [http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)    I try to open stream in VLC on Windows, and on Linux computer and  nothing. The VLC log gives me the same massage like before on Ubuntu  desktop.

Hi, what message are you getting in the VLC logs?

---

### Post by dejan-ciric-do on 2016-03-18
```
 [COLOR=#00008b]*core*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]cannot pre fill buffer
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "http"
 [COLOR=#00008b]*core*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot create a stream_t from access
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]finished input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 0/1)
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using item 0
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of the new playlist item
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on [http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]http://192.168.2.50:5005/udp/225.224.2.3:3003 is at 0
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'http://192.168.2.50:5005/udp/225.224.2.3:3003'
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]requesting art for [http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB, in path '/tmp'
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`[http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)' gives access `http' demux `' path `192.168.2.50:5005/udp/225.224.2.3:3003'
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]specified demux `any'
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='http' demux='any' location='192.168.2.50:5005/udp/225.224.2.3:3003' file='(null)'
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "http": 21 candidates
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access 'http' location='192.168.2.50:5005/udp/225.224.2.3:3003', path='(null)'
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "http": 25 candidates
 [COLOR=#00008b]*http*[/COLOR][COLOR=#808080]* debug: *[/COLOR]querying proxy for [http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*http*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no proxy
 [COLOR=#00008b]*http*[/COLOR][COLOR=#808080]* debug: *[/COLOR]http: server='192.168.2.50' port=5005 file='/udp/225.224.2.3:3003'
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]net: connecting to 192.168.2.50 port 5005
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]connection succeeded (socket = 26)
 [COLOR=#00008b]*http*[/COLOR][COLOR=#808080]* debug: *[/COLOR]protocol 'HTTP' answer code 200
 [COLOR=#00008b]*http*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Server: udpxy 1.0-23.9 (prod) standard [Linux 4.2.0-27-generic x86_64]
 [COLOR=#00008b]*http*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Content-Type: application/octet-stream
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using access module "http"
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Using stream method for AStream*
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting pre-buffering
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/tdnadmin/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]searching art for [http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/tdnadmin/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]art not found for [http://192.168.2.50:5005/udp/225.224.2.3:3003](http://192.168.2.50:5005/udp/225.224.2.3:3003)
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]incoming request - stopping current input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]object waitpipe triggered
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]socket 26 polling interrupted
 [COLOR=#00008b]*core*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]cannot pre fill buffer
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "http"
 [COLOR=#00008b]*core*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot create a stream_t from access
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]incoming request - stopping current input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]finished input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]incoming request - stopping current input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
```

---

