---
title: "grep and curl won't play nice together :/"
date: 2014-08-19
forum: Programming Talk
---

### Post by dev18 on 2014-08-19
Greetings,
     Kind of new around here, so hi. Recently, I've been playing the Twitch.tv api while learning Bash scripting. I'm trying simply to grep some keywords from the source of a page, but for some reason I can't get grep to follow the set commands for some reason. Like -A doesn't affect the output, -m doesn't, but -o does.

  Why doesn't this work? 

```

source=$(curl -s [https://api.twitch.tv/kraken/streams);](https://api.twitch.tv/kraken/streams);) printf "$source" | grep -m 1 -o "meclipse"
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse
meclipse

```

Example source:
```

606652,"language":"en"}},{"_id":10743589552,"game":"Smite","viewers":3037,"_links":{"self":"http://api.twitch.tv/kraken/streams/smitegame"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_smitegame-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_smitegame-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_smitegame-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_smitegame-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/smitegame","follows":"https://api.twitch.tv/kraken/channels/smitegame/follows","commercial":"https://api.twitch.tv/kraken/channels/smitegame/commercial","stream_key":"https://api.twitch.tv/kraken/channels/smitegame/stream_key","chat":"https://api.twitch.tv/kraken/chat/smitegame","features":"https://api.twitch.tv/kraken/channels/smitegame/features","subscriptions":"https://api.twitch.tv/kraken/channels/smitegame/subscriptions","editors":"https://api.twitch.tv/kraken/channels/smitegame/editors","videos":"https://api.twitch.tv/kraken/channels/smitegame/videos","teams":"https://api.twitch.tv/kraken/channels/smitegame/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/smitegame-channel_header_image-0bd76e5eb1ad0ca9-640x125.png","display_name":"Smitegame","game":"Smite","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/smitegame-profile_image-597d800b3d40e19f-300x300.png","mature":false,"status":"SMITE Lassiz - Learning how to play - Please tell me via chat","url":"http://www.twitch.tv/smitegame","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/smitegame-channel_offline_image-74e6fc4496e8b91a-640x360.jpeg","_id":31500812,"name":"smitegame","created_at":"2012-06-20T21:05:55Z","updated_at":"2014-08-20T00:29:22Z","abuse_reported":null,"delay":0,"followers":147385,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/smitegame-profile_banner-836ce0a2c03f0c5e-480.png","profile_banner_background_color":null,"views":87696165,"language":"en"}},{"_id":10742606448,"game":"World of Warcraft: Mists of Pandaria","viewers":2840,"_links":{"self":"https://api.twitch.tv/kraken/streams/swifty"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/swifty","follows":"https://api.twitch.tv/kraken/channels/swifty/follows","commercial":"https://api.twitch.tv/kraken/channels/swifty/commercial","stream_key":"https://api.twitch.tv/kraken/channels/swifty/stream_key","chat":"https://api.twitch.tv/kraken/chat/swifty","features":"https://api.twitch.tv/kraken/channels/swifty/features","subscriptions":"https://api.twitch.tv/kraken/channels/swifty/subscriptions","editors":"https://api.twitch.tv/kraken/channels/swifty/editors","videos":"https://api.twitch.tv/kraken/channels/swifty/videos","teams":"https://api.twitch.tv/kraken/channels/swifty/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/swifty-channel_header_image-c117d530a0546285-640x125.png","display_name":"Swifty","game":"World of Warcraft: Mists of Pandaria","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/swifty-profile_image-c8991452ac8ee48b-300x300.jpeg","mature":false,"status":"Swifty 24 Hour Livestream / WOD Keys Giveaways! Every 30 min! / WOD all day after Gym and Editing","url":"http://www.twitch.tv/swifty","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/swifty-channel_offline_image-ca421e997608d2de-640x360.jpeg","_id":23524577,"name":"swifty","created_at":"2011-07-18T02:06:46Z","updated_at":"2014-08-20T00:22:51Z","abuse_reported":null,"delay":0,"followers":272897,"profile_banner":null,"profile_banner_background_color":null,"views":27368184,"language":"en"}}],"_total":12857,"_links":{"self":"https://api.twitch.tv/kraken/streams?limit=25&offset=0","next":"https://api.twitch.tv/kraken/streams?limit=25&offset=25","featured":"https://api.twitch.tv/kraken/streams/featured","summary":"https://api.twitch.tv/kraken/streams/summary","followed":"https://api.twitch.tv/kraken/streams/followed"}}

```

---

### Post by steeldriver on 2014-08-19
what exactly are you trying to do? your "$sources" variable appears to consist of a single line, whereas grep is line-based

---

### Post by dev18 on 2014-08-19
> **steeldriver said:**
> what exactly are you trying to do? your "$sources" variable appears to consist of a single line, whereas grep is line-based

Thanks for looking into my problem steeldriver. What I want to do? Well, it's kind of a long story :D. Above, I'm curling the Twitch.tv api source which outputs some live streams. Then I grepped a streamer "meclipse." The output tells me they're live. I wanting to be able to grep my way through this curl data to get even more specifics. But the output is impossible to work with given my current issue with grep.

I made a pastebin of the curl output below, if that would help clarify things? Command at the top. Being grep is line-based, and the output is so convoluted and not spaced, it isn't able to read the data I'm looking for?

[http://pastebin.com/rAvjHQu7](http://pastebin.com/rAvjHQu7)

---

### Post by dev18 on 2014-08-19
For example, i grepped for 1 string. But the output gave me multiple and didn't stop at the first. 

command:
source=$(curl -s [https://api.twitch.tv/kraken/streams);](https://api.twitch.tv/kraken/streams);) printf "$source" | grep -m 1 "meclipse"

output:
ame":"playcevo","created_at":"2013-06-10T23:09:05Z","updated_at":"2014-08-20T02:17:00Z","abuse_reported":null,"delay":0,"followers":37389,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/playcevo-profile_banner-43ba426ee7b2fc4b-480.png","profile_banner_background_color":null,"views":3540319,"language":"en"}},{"_id":10740954384,"game":"Counter-Strike: Global Offensive","viewers":5094,"_links":{"self":"http://api.twitch.tv/kraken/streams/meclipse"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_meclipse-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_meclipse-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_**meclipse**-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_meclipse-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/meclipse","follows":"https://api.twitch.tv/kraken/channels/**meclipse**/follows","commercial":"https://api.twitch.tv/kraken/channels/meclipse/commercial","stream_key":"https://api.twitch.tv/kraken/channels/meclipse/stream_key","chat":"https://api.twitch.tv/kraken/chat/meclipse","features":"https://api.twitch.tv/kraken/channels/**meclipse**/features","subscriptions":"https://api.twitch.tv/kraken/channels/meclipse/subscriptions","editors":"https://api.twitch.tv/kraken/channels/**meclipse**/editors","videos":"https://api.twitch.tv/kraken/channels/meclipse/videos","teams":"https://api.twitch.tv/kraken/channels/**meclipse**/teams"},"background":null,"banner":null,"display_name":"mEclipse","game":"Counter-Strike: Global Offensive","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/meclipse-profile_image-0373ffcdea347024-300x300.jpeg","mature":true,"status":"C9 shroud, CSGO MM!? | Follow @C9shroud","url":"http://www.twitch.tv/meclipse","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/**meclipse**-channel_offline_image-8e9fea85d5ce75af-640x360.png","_id":37402112,"name":"**meclipse**","created_at":"2012-11-03T15:50:32Z","updated_at":"2014-08-20T02:04:50Z","abuse_reported":null,"delay":0,"followers":52453,"profile_banner":null,"profile_banner_background_color":null,"views":2923042,"language":"en"}},{"_id":10744067360,"game":"Super Smash Bros. Melee","viewers":4416,"_links":{"self":"https://api.twitch.tv/kraken/streams/vgbootcamp"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_vgbootcamp-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_vgbootcamp-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_vgbootcamp-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_vgbootcamp-{width}x{he

---

### Post by steeldriver on 2014-08-19
-o prints each of the matching patterns on a separate line, and -m 1 stops after 1 matched **line** - so it's doing exactly what it says on the tin, I think

See `man grep`

```

       -m NUM, --max-count=NUM
              Stop reading a file after NUM matching lines.  If the  input  is
              standard  input  from a regular file, and NUM matching lines are
              output, grep ensures that the standard input  is  positioned  to
              just  after the last matching line before exiting, regardless of
              the presence of trailing context lines.  This enables a  calling
              process  to resume a search.  When grep stops after NUM matching
              lines, it outputs any trailing context lines.  When  the  -c  or
              --count  option  is  also  used,  grep  does  not output a count
              greater than NUM.  When the -v or --invert-match option is  also
              used, grep stops after outputting NUM non-matching lines.

       -o, --only-matching
              Print  only  the  matched  (non-empty) parts of a matching line,
              with each such part on a separate output line.

```

---

### Post by steeldriver on 2014-08-19
-o prints each of the matching patterns on a separate line, and -m 1 stops after 1 matched **line** - so it's doing exactly what it says on the tin, I think

See `man grep`

```

       -m NUM, --max-count=NUM
              Stop reading a file after NUM matching lines.  If the  input  is
              standard  input  from a regular file, and NUM matching lines are
              output, grep ensures that the standard input  is  positioned  to
              just  after the last matching line before exiting, regardless of
              the presence of trailing context lines.  This enables a  calling
              process  to resume a search.  When grep stops after NUM matching
              lines, it outputs any trailing context lines.  When  the  -c  or
              --count  option  is  also  used,  grep  does  not output a count
              greater than NUM.  When the -v or --invert-match option is  also
              used, grep stops after outputting NUM non-matching lines.

       -o, --only-matching
              Print  only  the  matched  (non-empty) parts of a matching line,
              with each such part on a separate output line.

```

---

### Post by dev18 on 2014-08-19
I think your right steel. 

Command:
source=$(curl -s [www.google.com);]("http://www.google.com);") echo "$source" | grep -m 1 -o "g"
Output:
g
g
...
...

Although, using the -m argument with a system function seems to work...  

Command:
ls | grep -m 1 "D"
Output:
Desktop

Where: ls | grep -c "D" outputs a value of 4 (Documents etc.) So any ideas how to make it work with a curl output? :D (Getting there)

---

### Post by CantankRus on 2014-08-20
The output from your **source=$(curl -s [https://api.twitch.tv/kraken/streams);](https://api.twitch.tv/kraken/streams);) printf "$source"** command is a single line which wraps around in the terminal.
Send it to a text file and see.
```
curl -s https://api.twitch.tv/kraken/streams > test.txt
```

grep prints the matching lines and -c counts the matched lines.

eg "profile" is matched numerous times but they're all in the same line.
```
@Trusty:~$ curl -s https://api.twitch.tv/kraken/streams | grep profile
{"streams":[{"_id":10745823264,"game":"Hearthstone: Heroes of Warcraft","viewers":13248,"_links":{"self":"https://api.twitch.tv/kraken/streams/nl_kripp"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_nl_kripp-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_nl_kripp-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_nl_kripp-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_nl_kripp-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/nl_kripp","follows":"https://api.twitch.tv/kraken/channels/nl_kripp/follows","commercial":"https://api.twitch.tv/kraken/channels/nl_kripp/commercial","stream_key":"https://api.twitch.tv/kraken/channels/nl_kripp/stream_key","chat":"https://api.twitch.tv/kraken/chat/nl_kripp","features":"https://api.twitch.tv/kraken/channels/nl_kripp/features","subscriptions":"https://api.twitch.tv/kraken/channels/nl_kripp/subscriptions","editors":"https://api.twitch.tv/kraken/channels/nl_kripp/editors","videos":"https://api.twitch.tv/kraken/channels/nl_kripp/videos","teams":"https://api.twitch.tv/kraken/channels/nl_kripp/teams"},"background":null,"banner":null,"display_name":"nl_Kripp","game":"Hearthstone: Heroes of Warcraft","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/nl_kripp-profile_image-267fd5e2fb95a15d-300x300.png","mature":false,"status":"nolife Kripp -- \u30fd\u0f3c\u2611\u0644\u035c\u2611\u0f3d\uff89 No Naxx Day Because of Downtime /sad","url":"http://www.twitch.tv/nl_kripp","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/nl_kripp-channel_offline_image-f3ad1124bc19cffd-640x360.png","_id":29795919,"name":"nl_kripp","created_at":"2012-04-15T02:25:31Z","updated_at":"2014-08-20T04:36:13Z","abuse_reported":null,"delay":0,"followers":285012,"profile_banner":null,"profile_banner_background_color":null,"views":87193591,"language":"en"}},{"_id":10745015584,"game":"League of Legends","viewers":12968,"_links":{"self":"https://api.twitch.tv/kraken/streams/trick2g"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_trick2g-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_trick2g-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_trick2g-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_trick2g-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/trick2g","follows":"https://api.twitch.tv/kraken/channels/trick2g/follows","commercial":"https://api.twitch.tv/kraken/channels/trick2g/commercial","stream_key":"https://api.twitch.tv/kraken/channels/trick2g/stream_key","chat":"https://api.twitch.tv/kraken/chat/trick2g","features":"https://api.twitch.tv/kraken/channels/trick2g/features","subscriptions":"https://api.twitch.tv/kraken/channels/trick2g/subscriptions","editors":"https://api.twitch.tv/kraken/channels/trick2g/editors","videos":"https://api.twitch.tv/kraken/channels/trick2g/videos","teams":"https://api.twitch.tv/kraken/channels/trick2g/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/trick2g-channel_header_image-a712bd1af57ae2ee-640x125.jpeg","display_name":"Trick2g","game":"League of Legends","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/trick2g-profile_image-4f7802d5130b20e9-300x300.png","mature":true,"status":"Godyr | New way of doing Specs + Subwars | Wow Cant Believe I didnt think of this sooner | Still2g","url":"http://www.twitch.tv/trick2g","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/trick2g-channel_offline_image-2e7445fb1944e6bf-640x360.png","_id":28036688,"name":"trick2g","created_at":"2012-02-06T21:16:52Z","updated_at":"2014-08-20T01:28:24Z","abuse_reported":null,"delay":0,"followers":458776,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/trick2g-profile_banner-d326186fdd09f433-480.jpeg","profile_banner_background_color":"#030303","views":63273047,"language":"en"}},{"_id":10746929376,"game":"League of Legends","viewers":11143,"_links":{"self":"https://api.twitch.tv/kraken/streams/scarra"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_scarra-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_scarra-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_scarra-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_scarra-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/scarra","follows":"https://api.twitch.tv/kraken/channels/scarra/follows","commercial":"https://api.twitch.tv/kraken/channels/scarra/commercial","stream_key":"https://api.twitch.tv/kraken/channels/scarra/stream_key","chat":"https://api.twitch.tv/kraken/chat/scarra","features":"https://api.twitch.tv/kraken/channels/scarra/features","subscriptions":"https://api.twitch.tv/kraken/channels/scarra/subscriptions","editors":"https://api.twitch.tv/kraken/channels/scarra/editors","videos":"https://api.twitch.tv/kraken/channels/scarra/videos","teams":"https://api.twitch.tv/kraken/channels/scarra/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/scarra-channel_header_image-ded20a1cfc7100dc-640x125.jpeg","display_name":"Scarra","game":"League of Legends","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/scarra-profile_image-4b53a66f666717b2-300x300.jpeg","mature":false,"status":"Scarra's Stream | Duo with altec | Hearthstone in Q | Till midnight","url":"http://www.twitch.tv/scarra","video_banner":null,"_id":22253819,"name":"scarra","created_at":"2011-05-07T09:53:48Z","updated_at":"2014-08-20T04:32:05Z","abuse_reported":null,"delay":0,"followers":214106,"profile_banner":null,"profile_banner_background_color":null,"views":32287333,"language":"en"}},{"_id":10745338112,"game":"Dota 2","viewers":10595,"_links":{"self":"https://api.twitch.tv/kraken/streams/arteezy"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_arteezy-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_arteezy-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_arteezy-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_arteezy-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/arteezy","follows":"http://api.twitch.tv/kraken/channels/arteezy/follows","commercial":"http://api.twitch.tv/kraken/channels/arteezy/commercial","stream_key":"http://api.twitch.tv/kraken/channels/arteezy/stream_key","chat":"http://api.twitch.tv/kraken/chat/arteezy","features":"http://api.twitch.tv/kraken/channels/arteezy/features","subscriptions":"http://api.twitch.tv/kraken/channels/arteezy/subscriptions","editors":"http://api.twitch.tv/kraken/channels/arteezy/editors","videos":"http://api.twitch.tv/kraken/channels/arteezy/videos","teams":"http://api.twitch.tv/kraken/channels/arteezy/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/arteezy-channel_header_image-cad3dbf202e08368-640x125.png","display_name":"Arteezy","game":"Dota 2","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/arteezy-profile_image-7fb0836472c2dfe3-300x300.png","mature":false,"status":"EG.Arteezy playing nel - waiting for the game to end ","url":"http://www.twitch.tv/arteezy","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/arteezy-channel_offline_image-bf05cd1f74339ee2-640x360.jpeg","_id":23364603,"name":"arteezy","created_at":"2011-07-09T22:27:08Z","updated_at":"2014-08-20T03:07:39Z","abuse_reported":null,"delay":0,"followers":75452,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/arteezy-profile_banner-9157e5374f6e81f0-480.jpeg","profile_banner_background_color":"null","views":12169395,"language":"en"}},{"_id":10746242896,"game":"The Last of Us","viewers":9231,"_links":{"self":"https://api.twitch.tv/kraken/streams/goldglove"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_goldglove-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_goldglove-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_goldglove-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_goldglove-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/goldglove","follows":"http://api.twitch.tv/kraken/channels/goldglove/follows","commercial":"http://api.twitch.tv/kraken/channels/goldglove/commercial","stream_key":"http://api.twitch.tv/kraken/channels/goldglove/stream_key","chat":"http://api.twitch.tv/kraken/chat/goldglove","features":"http://api.twitch.tv/kraken/channels/goldglove/features","subscriptions":"http://api.twitch.tv/kraken/channels/goldglove/subscriptions","editors":"http://api.twitch.tv/kraken/channels/goldglove/editors","videos":"http://api.twitch.tv/kraken/channels/goldglove/videos","teams":"http://api.twitch.tv/kraken/channels/goldglove/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/goldglove-channel_header_image-1cfd78393ea7c58f-640x125.png","display_name":"GoldGlove","game":"The Last of Us","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/goldglove-profile_image-15000ece6aee7cd7-300x300.png","mature":false,"status":"Playin' Da Games w/ Goldy","url":"http://www.twitch.tv/goldglove","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/goldglove-channel_offline_image-1f481d47dd688905-640x360.png","_id":1518077,"name":"goldglove","created_at":"2008-08-26T05:35:21Z","updated_at":"2014-08-20T05:28:36Z","abuse_reported":null,"delay":0,"followers":405396,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/goldglove-profile_banner-fa4d48418df5593d-480.jpeg","profile_banner_background_color":null,"views":19497328,"language":"en"}},{"_id":10745040656,"game":"Minecraft","viewers":6816,"_links":{"self":"https://api.twitch.tv/kraken/streams/bacon_donut"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_bacon_donut-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_bacon_donut-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_bacon_donut-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_bacon_donut-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/bacon_donut","follows":"https://api.twitch.tv/kraken/channels/bacon_donut/follows","commercial":"https://api.twitch.tv/kraken/channels/bacon_donut/commercial","stream_key":"https://api.twitch.tv/kraken/channels/bacon_donut/stream_key","chat":"https://api.twitch.tv/kraken/chat/bacon_donut","features":"https://api.twitch.tv/kraken/channels/bacon_donut/features","subscriptions":"https://api.twitch.tv/kraken/channels/bacon_donut/subscriptions","editors":"https://api.twitch.tv/kraken/channels/bacon_donut/editors","videos":"https://api.twitch.tv/kraken/channels/bacon_donut/videos","teams":"https://api.twitch.tv/kraken/channels/bacon_donut/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/bacon_donut-channel_header_image-85809e3381b9380b-640x125.png","display_name":"Bacon_Donut","game":"Minecraft","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/bacon_donut-profile_image-4c7853beb3247b30-300x300.png","mature":false,"status":"[Bacon] Crash Landing 1.1.2 Hardcore Single Player! WITH BACON!!!!!!","url":"http://www.twitch.tv/bacon_donut","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/bacon_donut-channel_offline_image-054855daba7ea79c-640x360.png","_id":36155872,"name":"bacon_donut","created_at":"2012-09-13T22:11:28Z","updated_at":"2014-08-20T04:57:24Z","abuse_reported":null,"delay":0,"followers":232158,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/bacon_donut-profile_banner-b4376e703de7e67b-480.jpeg","profile_banner_background_color":null,"views":11894990,"language":"en"}},{"_id":10746727616,"game":"The Last of Us","viewers":5385,"_links":{"self":"https://api.twitch.tv/kraken/streams/mym_alkapone"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_mym_alkapone-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_mym_alkapone-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_mym_alkapone-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_mym_alkapone-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/mym_alkapone","follows":"https://api.twitch.tv/kraken/channels/mym_alkapone/follows","commercial":"https://api.twitch.tv/kraken/channels/mym_alkapone/commercial","stream_key":"https://api.twitch.tv/kraken/channels/mym_alkapone/stream_key","chat":"https://api.twitch.tv/kraken/chat/mym_alkapone","features":"https://api.twitch.tv/kraken/channels/mym_alkapone/features","subscriptions":"https://api.twitch.tv/kraken/channels/mym_alkapone/subscriptions","editors":"https://api.twitch.tv/kraken/channels/mym_alkapone/editors","videos":"https://api.twitch.tv/kraken/channels/mym_alkapone/videos","teams":"https://api.twitch.tv/kraken/channels/mym_alkapone/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/mym_alkapone-channel_header_image-b6fc2e2a9ab3507f-640x125.jpeg","display_name":"MYM_ALKAPONE","game":"The Last of Us","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/mym_alkapone-profile_image-f1a53911f30e7063-300x300.jpeg","mature":true,"status":"The Last of Us Remake Ep. 6 I Vota MYM_ALKAPONE INTL.gg I ","url":"http://www.twitch.tv/mym_alkapone","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/mym_alkapone-channel_offline_image-07550a71a3ee73e1-640x360.jpeg","_id":31478096,"name":"mym_alkapone","created_at":"2012-06-19T22:03:04Z","updated_at":"2014-08-20T05:34:11Z","abuse_reported":null,"delay":0,"followers":92141,"profile_banner":null,"profile_banner_background_color":null,"views":5380209,"language":"es"}},{"_id":10743824832,"game":"Dark Souls II","viewers":4985,"_links":{"self":"https://api.twitch.tv/kraken/streams/manvsgame"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_manvsgame-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_manvsgame-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_manvsgame-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_manvsgame-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/manvsgame","follows":"https://api.twitch.tv/kraken/channels/manvsgame/follows","commercial":"https://api.twitch.tv/kraken/channels/manvsgame/commercial","stream_key":"https://api.twitch.tv/kraken/channels/manvsgame/stream_key","chat":"https://api.twitch.tv/kraken/chat/manvsgame","features":"https://api.twitch.tv/kraken/channels/manvsgame/features","subscriptions":"https://api.twitch.tv/kraken/channels/manvsgame/subscriptions","editors":"https://api.twitch.tv/kraken/channels/manvsgame/editors","videos":"https://api.twitch.tv/kraken/channels/manvsgame/videos","teams":"https://api.twitch.tv/kraken/channels/manvsgame/teams"},"background":null,"banner":null,"display_name":"MANvsGAME","game":"Dark Souls II","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/manvsgame-profile_image-b90a89f4bc2beeda-300x300.png","mature":true,"status":"MAN vs DARK SOULS II (PC) NG+++ Champions Covenant","url":"http://www.twitch.tv/manvsgame","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/manvsgame-channel_offline_image-dac06b43c3cf5f37-640x360.jpeg","_id":8330235,"name":"manvsgame","created_at":"2009-09-17T19:42:52Z","updated_at":"2014-08-20T00:19:14Z","abuse_reported":null,"delay":0,"followers":239228,"profile_banner":null,"profile_banner_background_color":"null","views":41383970,"language":"en"}},{"_id":10746077744,"game":"League of Legends","viewers":4361,"_links":{"self":"http://api.twitch.tv/kraken/streams/sirhcez"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sirhcez-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sirhcez-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sirhcez-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sirhcez-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/sirhcez","follows":"https://api.twitch.tv/kraken/channels/sirhcez/follows","commercial":"https://api.twitch.tv/kraken/channels/sirhcez/commercial","stream_key":"https://api.twitch.tv/kraken/channels/sirhcez/stream_key","chat":"https://api.twitch.tv/kraken/chat/sirhcez","features":"https://api.twitch.tv/kraken/channels/sirhcez/features","subscriptions":"https://api.twitch.tv/kraken/channels/sirhcez/subscriptions","editors":"https://api.twitch.tv/kraken/channels/sirhcez/editors","videos":"https://api.twitch.tv/kraken/channels/sirhcez/videos","teams":"https://api.twitch.tv/kraken/channels/sirhcez/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/sirhcez-channel_header_image-b048d0787bb08d80-640x125.jpeg","display_name":"SirhcEz","game":"League of Legends","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/sirhcez-profile_image-3f7425fa389123c1-300x300.jpeg","mature":false,"status":"SirhcEz - DeathCap Singed | LifeSteal Nasus | How to Stack Qs","url":"http://www.twitch.tv/sirhcez","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/sirhcez-channel_offline_image-869ec7f587ffab7c-640x360.jpeg","_id":27934574,"name":"sirhcez","created_at":"2012-02-03T09:05:18Z","updated_at":"2014-08-20T04:54:07Z","abuse_reported":null,"delay":0,"followers":233737,"profile_banner":null,"profile_banner_background_color":null,"views":33920905,"language":"en"}},{"_id":10747152128,"game":"League of Legends","viewers":3803,"_links":{"self":"https://api.twitch.tv/kraken/streams/hail9"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_hail9-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_hail9-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_hail9-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_hail9-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/hail9","follows":"https://api.twitch.tv/kraken/channels/hail9/follows","commercial":"https://api.twitch.tv/kraken/channels/hail9/commercial","stream_key":"https://api.twitch.tv/kraken/channels/hail9/stream_key","chat":"https://api.twitch.tv/kraken/chat/hail9","features":"https://api.twitch.tv/kraken/channels/hail9/features","subscriptions":"https://api.twitch.tv/kraken/channels/hail9/subscriptions","editors":"https://api.twitch.tv/kraken/channels/hail9/editors","videos":"https://api.twitch.tv/kraken/channels/hail9/videos","teams":"https://api.twitch.tv/kraken/channels/hail9/teams"},"background":null,"banner":null,"display_name":"HaiL9","game":"League of Legends","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/hail9-profile_image-303e525202f2fcfe-300x300.jpeg","mature":false,"status":"C9 HyperX Hai~ Challenger!","url":"http://www.twitch.tv/hail9","video_banner":null,"_id":28631766,"name":"hail9","created_at":"2012-03-01T16:39:37Z","updated_at":"2014-08-20T05:04:56Z","abuse_reported":null,"delay":0,"followers":146863,"profile_banner":null,"profile_banner_background_color":null,"views":12423871,"language":"en"}},{"_id":10746202496,"game":"World of Warcraft: Mists of Pandaria","viewers":3076,"_links":{"self":"https://api.twitch.tv/kraken/streams/swifty"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_swifty-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/swifty","follows":"https://api.twitch.tv/kraken/channels/swifty/follows","commercial":"https://api.twitch.tv/kraken/channels/swifty/commercial","stream_key":"https://api.twitch.tv/kraken/channels/swifty/stream_key","chat":"https://api.twitch.tv/kraken/chat/swifty","features":"https://api.twitch.tv/kraken/channels/swifty/features","subscriptions":"https://api.twitch.tv/kraken/channels/swifty/subscriptions","editors":"https://api.twitch.tv/kraken/channels/swifty/editors","videos":"https://api.twitch.tv/kraken/channels/swifty/videos","teams":"https://api.twitch.tv/kraken/channels/swifty/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/swifty-channel_header_image-c117d530a0546285-640x125.png","display_name":"Swifty","game":"World of Warcraft: Mists of Pandaria","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/swifty-profile_image-c8991452ac8ee48b-300x300.jpeg","mature":false,"status":"Swifty 24 Hour Livestream / WOD Keys Giveaways! Every 30 min! / WOD all day after Gym and Editing","url":"http://www.twitch.tv/swifty","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/swifty-channel_offline_image-ca421e997608d2de-640x360.jpeg","_id":23524577,"name":"swifty","created_at":"2011-07-18T02:06:46Z","updated_at":"2014-08-20T03:04:01Z","abuse_reported":null,"delay":0,"followers":273166,"profile_banner":null,"profile_banner_background_color":null,"views":27368184,"language":"en"}},{"_id":10746292320,"game":"Hearthstone: Heroes of Warcraft","viewers":3031,"_links":{"self":"https://api.twitch.tv/kraken/streams/sjow"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sjow-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sjow-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sjow-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_sjow-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/sjow","follows":"http://api.twitch.tv/kraken/channels/sjow/follows","commercial":"http://api.twitch.tv/kraken/channels/sjow/commercial","stream_key":"http://api.twitch.tv/kraken/channels/sjow/stream_key","chat":"http://api.twitch.tv/kraken/chat/sjow","features":"http://api.twitch.tv/kraken/channels/sjow/features","subscriptions":"http://api.twitch.tv/kraken/channels/sjow/subscriptions","editors":"http://api.twitch.tv/kraken/channels/sjow/editors","videos":"http://api.twitch.tv/kraken/channels/sjow/videos","teams":"http://api.twitch.tv/kraken/channels/sjow/teams"},"background":null,"banner":null,"display_name":"Sjow","game":"Hearthstone: Heroes of Warcraft","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/sjow-profile_image-a3cf0b01219b33c4-300x300.jpeg","mature":true,"status":"Rank 1 EU going for #1 NA now!","url":"http://www.twitch.tv/sjow","video_banner":null,"_id":22588033,"name":"sjow","created_at":"2011-05-24T22:03:27Z","updated_at":"2014-08-20T03:14:10Z","abuse_reported":null,"delay":0,"followers":12471,"profile_banner":null,"profile_banner_background_color":null,"views":1555204,"language":"sv"}},{"_id":10744829248,"game":"Mafia LIVE!","viewers":3008,"_links":{"self":"https://api.twitch.tv/kraken/streams/ryuzilla"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_ryuzilla-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_ryuzilla-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_ryuzilla-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_ryuzilla-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/ryuzilla","follows":"http://api.twitch.tv/kraken/channels/ryuzilla/follows","commercial":"http://api.twitch.tv/kraken/channels/ryuzilla/commercial","stream_key":"http://api.twitch.tv/kraken/channels/ryuzilla/stream_key","chat":"http://api.twitch.tv/kraken/chat/ryuzilla","features":"http://api.twitch.tv/kraken/channels/ryuzilla/features","subscriptions":"http://api.twitch.tv/kraken/channels/ryuzilla/subscriptions","editors":"http://api.twitch.tv/kraken/channels/ryuzilla/editors","videos":"http://api.twitch.tv/kraken/channels/ryuzilla/videos","teams":"http://api.twitch.tv/kraken/channels/ryuzilla/teams"},"background":null,"banner":null,"display_name":"Ryuzilla","game":"Mafia LIVE!","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/ryuzilla-profile_image-32aa91e0b00c6187-300x300.png","mature":true,"status":"Super Mafia All-Stars! ","url":"http://www.twitch.tv/ryuzilla","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/ryuzilla-channel_offline_image-3739c64db4c0ecd5-640x360.png","_id":44473716,"name":"ryuzilla","created_at":"2013-06-08T03:08:19Z","updated_at":"2014-08-20T01:04:42Z","abuse_reported":null,"delay":0,"followers":21218,"profile_banner":null,"profile_banner_background_color":null,"views":1740135,"language":"en"}},{"_id":10745473232,"game":"StarCraft II: Heart of the Swarm","viewers":2791,"_links":{"self":"https://api.twitch.tv/kraken/streams/zlfreebird"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_zlfreebird-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_zlfreebird-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_zlfreebird-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_zlfreebird-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/zlfreebird","follows":"http://api.twitch.tv/kraken/channels/zlfreebird/follows","commercial":"http://api.twitch.tv/kraken/channels/zlfreebird/commercial","stream_key":"http://api.twitch.tv/kraken/channels/zlfreebird/stream_key","chat":"http://api.twitch.tv/kraken/chat/zlfreebird","features":"http://api.twitch.tv/kraken/channels/zlfreebird/features","subscriptions":"http://api.twitch.tv/kraken/channels/zlfreebird/subscriptions","editors":"http://api.twitch.tv/kraken/channels/zlfreebird/editors","videos":"http://api.twitch.tv/kraken/channels/zlfreebird/videos","teams":"http://api.twitch.tv/kraken/channels/zlfreebird/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/zlfreebird-channel_header_image-f5379060177eeb25-640x125.png","display_name":"zLfreebird","game":"StarCraft II: Heart of the Swarm","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/zlfreebird-profile_image-4d5464cca009fb7a-300x300.png","mature":false,"status":"WinterSC - Learn to play StarCraft","url":"http://www.twitch.tv/zlfreebird","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/zlfreebird-channel_offline_image-35b83bd49e6c375c-640x360.png","_id":25766032,"name":"zlfreebird","created_at":"2011-10-28T05:57:08Z","updated_at":"2014-08-20T01:49:17Z","abuse_reported":null,"delay":0,"followers":32599,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/zlfreebird-profile_banner-3bab59572df3bf03-480.jpeg","profile_banner_background_color":null,"views":2880622,"language":"en"}},{"_id":10746304800,"game":"Dota 2","viewers":2305,"_links":{"self":"https://api.twitch.tv/kraken/streams/feardarkness"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_feardarkness-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_feardarkness-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_feardarkness-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_feardarkness-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/feardarkness","follows":"http://api.twitch.tv/kraken/channels/feardarkness/follows","commercial":"http://api.twitch.tv/kraken/channels/feardarkness/commercial","stream_key":"http://api.twitch.tv/kraken/channels/feardarkness/stream_key","chat":"http://api.twitch.tv/kraken/chat/feardarkness","features":"http://api.twitch.tv/kraken/channels/feardarkness/features","subscriptions":"http://api.twitch.tv/kraken/channels/feardarkness/subscriptions","editors":"http://api.twitch.tv/kraken/channels/feardarkness/editors","videos":"http://api.twitch.tv/kraken/channels/feardarkness/videos","teams":"http://api.twitch.tv/kraken/channels/feardarkness/teams"},"background":null,"banner":null,"display_name":"FearDarkness","game":"Dota 2","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/feardarkness-profile_image-3506ec69418398cc-300x300.jpeg","mature":null,"status":"Nah, this for me doe","url":"http://www.twitch.tv/feardarkness","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/feardarkness-channel_offline_image-8aa891f83dcce972-640x360.jpeg","_id":25095238,"name":"feardarkness","created_at":"2011-09-26T21:36:09Z","updated_at":"2014-08-20T03:15:53Z","abuse_reported":null,"delay":0,"followers":34823,"profile_banner":null,"profile_banner_background_color":null,"views":5987606,"language":"en"}},{"_id":10746776224,"game":"Outlast","viewers":2077,"_links":{"self":"https://api.twitch.tv/kraken/streams/destiny"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_destiny-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_destiny-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_destiny-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_destiny-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/destiny","follows":"https://api.twitch.tv/kraken/channels/destiny/follows","commercial":"https://api.twitch.tv/kraken/channels/destiny/commercial","stream_key":"https://api.twitch.tv/kraken/channels/destiny/stream_key","chat":"https://api.twitch.tv/kraken/chat/destiny","features":"https://api.twitch.tv/kraken/channels/destiny/features","subscriptions":"https://api.twitch.tv/kraken/channels/destiny/subscriptions","editors":"https://api.twitch.tv/kraken/channels/destiny/editors","videos":"https://api.twitch.tv/kraken/channels/destiny/videos","teams":"https://api.twitch.tv/kraken/channels/destiny/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/destiny-channel_header_image-d2b9b2452f67ec00-640x125.jpeg","display_name":"Destiny","game":"Outlast","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/destiny-profile_image-951fd53950bc2f8b-300x300.png","mature":true,"status":"Destiny - Why can't I kill the monsters :( - http://www.destiny.gg/bigscreen","url":"http://www.twitch.tv/destiny","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/destiny-channel_offline_image-6db50603ddebf576-640x360.png","_id":18074328,"name":"destiny","created_at":"2010-11-22T04:14:56Z","updated_at":"2014-08-20T04:08:37Z","abuse_reported":null,"delay":0,"followers":91174,"profile_banner":null,"profile_banner_background_color":null,"views":58243599,"language":"en"}},{"_id":10746700000,"game":"World of Warcraft: Mists of Pandaria","viewers":2018,"_links":{"self":"https://api.twitch.tv/kraken/streams/watchmeblink1"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_watchmeblink1-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_watchmeblink1-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_watchmeblink1-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_watchmeblink1-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/watchmeblink1","follows":"http://api.twitch.tv/kraken/channels/watchmeblink1/follows","commercial":"http://api.twitch.tv/kraken/channels/watchmeblink1/commercial","stream_key":"http://api.twitch.tv/kraken/channels/watchmeblink1/stream_key","chat":"http://api.twitch.tv/kraken/chat/watchmeblink1","features":"http://api.twitch.tv/kraken/channels/watchmeblink1/features","subscriptions":"http://api.twitch.tv/kraken/channels/watchmeblink1/subscriptions","editors":"http://api.twitch.tv/kraken/channels/watchmeblink1/editors","videos":"http://api.twitch.tv/kraken/channels/watchmeblink1/videos","teams":"http://api.twitch.tv/kraken/channels/watchmeblink1/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/watchmeblink1-channel_header_image-82ca24b94272dbd7-640x125.jpeg","display_name":"Watchmeblink1","game":"World of Warcraft: Mists of Pandaria","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/watchmeblink1-profile_image-8d7a8875556ca08d-300x300.png","mature":false,"status":"<Mitchjones> - OLD SCHOOL RMD","url":"http://www.twitch.tv/watchmeblink1","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/watchmeblink1-channel_offline_image-1e1df2eca0dacbb6-640x360.jpeg","_id":26194208,"name":"watchmeblink1","created_at":"2011-11-17T09:20:52Z","updated_at":"2014-08-20T04:03:11Z","abuse_reported":null,"delay":0,"followers":45015,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/watchmeblink1-profile_banner-e2da05549112f3fb-480.jpeg","profile_banner_background_color":"null","views":5006104,"language":"en"}},{"_id":10746574768,"game":"Call of Duty: Black Ops II","viewers":2016,"_links":{"self":"https://api.twitch.tv/kraken/streams/maximilian_dood"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_maximilian_dood-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_maximilian_dood-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_maximilian_dood-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_maximilian_dood-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/maximilian_dood","follows":"https://api.twitch.tv/kraken/channels/maximilian_dood/follows","commercial":"https://api.twitch.tv/kraken/channels/maximilian_dood/commercial","stream_key":"https://api.twitch.tv/kraken/channels/maximilian_dood/stream_key","chat":"https://api.twitch.tv/kraken/chat/maximilian_dood","features":"https://api.twitch.tv/kraken/channels/maximilian_dood/features","subscriptions":"https://api.twitch.tv/kraken/channels/maximilian_dood/subscriptions","editors":"https://api.twitch.tv/kraken/channels/maximilian_dood/editors","videos":"https://api.twitch.tv/kraken/channels/maximilian_dood/videos","teams":"https://api.twitch.tv/kraken/channels/maximilian_dood/teams"},"background":null,"banner":null,"display_name":"Maximilian_DOOD","game":"Call of Duty: Black Ops II","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/maximilian_dood-profile_image-c6e12e1798861491-300x300.png","mature":false,"status":"CALLADOOTY - Come Join! X360 - Slightly Sick - Relaxing w/Max","url":"http://www.twitch.tv/maximilian_dood","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/maximilian_dood-channel_offline_image-4ef79b6e1d24c4bd-640x360.jpeg","_id":30104304,"name":"maximilian_dood","created_at":"2012-04-28T03:03:56Z","updated_at":"2014-08-20T03:44:08Z","abuse_reported":null,"delay":0,"followers":55096,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/maximilian_dood-profile_banner-d1fc30805e005354-480.jpeg","profile_banner_background_color":"#000000","views":2262030,"language":null}},{"_id":10747204000,"game":"League of Legends","viewers":1973,"_links":{"self":"https://api.twitch.tv/kraken/streams/itshafu"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_itshafu-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_itshafu-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_itshafu-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_itshafu-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/itshafu","follows":"http://api.twitch.tv/kraken/channels/itshafu/follows","commercial":"http://api.twitch.tv/kraken/channels/itshafu/commercial","stream_key":"http://api.twitch.tv/kraken/channels/itshafu/stream_key","chat":"http://api.twitch.tv/kraken/chat/itshafu","features":"http://api.twitch.tv/kraken/channels/itshafu/features","subscriptions":"http://api.twitch.tv/kraken/channels/itshafu/subscriptions","editors":"http://api.twitch.tv/kraken/channels/itshafu/editors","videos":"http://api.twitch.tv/kraken/channels/itshafu/videos","teams":"http://api.twitch.tv/kraken/channels/itshafu/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/itshafu-channel_header_image-570bbd1074674e16-640x125.png","display_name":"itsHafu","game":"League of Legends","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/itshafu-profile_image-1c424631f99d8f02-300x300.jpeg","mature":false,"status":"Hafu - duo w/ ETLIAAAAAaaaahhhhhh","url":"http://www.twitch.tv/itshafu","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/itshafu-channel_offline_image-90514e2e596cfcb9-640x360.jpeg","_id":30777889,"name":"itshafu","created_at":"2012-05-24T19:36:36Z","updated_at":"2014-08-20T05:12:47Z","abuse_reported":null,"delay":0,"followers":212622,"profile_banner":null,"profile_banner_background_color":null,"views":33454186,"language":"en"}},{"_id":10745687776,"game":"League of Legends","viewers":1861,"_links":{"self":"https://api.twitch.tv/kraken/streams/s982121"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_s982121-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_s982121-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_s982121-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_s982121-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/s982121","follows":"http://api.twitch.tv/kraken/channels/s982121/follows","commercial":"http://api.twitch.tv/kraken/channels/s982121/commercial","stream_key":"http://api.twitch.tv/kraken/channels/s982121/stream_key","chat":"http://api.twitch.tv/kraken/chat/s982121","features":"http://api.twitch.tv/kraken/channels/s982121/features","subscriptions":"http://api.twitch.tv/kraken/channels/s982121/subscriptions","editors":"http://api.twitch.tv/kraken/channels/s982121/editors","videos":"http://api.twitch.tv/kraken/channels/s982121/videos","teams":"http://api.twitch.tv/kraken/channels/s982121/teams"},"background":null,"banner":null,"display_name":"s982121","game":"League of Legends","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/s982121-profile_image-f41a2d567e110432-300x300.jpeg","mature":false,"status":"\u6771\u6d77\u5d14\u52dd\u8ce2\r\n\r\n\r\n","url":"http://www.twitch.tv/s982121","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/s982121-channel_offline_image-84f43179096c7892-640x360.jpeg","_id":42775389,"name":"s982121","created_at":"2013-04-23T08:07:27Z","updated_at":"2014-08-20T02:11:09Z","abuse_reported":null,"delay":0,"followers":29350,"profile_banner":null,"profile_banner_background_color":null,"views":3242160,"language":"en"}},{"_id":10746960352,"game":"Smite","viewers":1680,"_links":{"self":"https://api.twitch.tv/kraken/streams/dmbrandon"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_dmbrandon-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_dmbrandon-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_dmbrandon-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_dmbrandon-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/dmbrandon","follows":"https://api.twitch.tv/kraken/channels/dmbrandon/follows","commercial":"https://api.twitch.tv/kraken/channels/dmbrandon/commercial","stream_key":"https://api.twitch.tv/kraken/channels/dmbrandon/stream_key","chat":"https://api.twitch.tv/kraken/chat/dmbrandon","features":"https://api.twitch.tv/kraken/channels/dmbrandon/features","subscriptions":"https://api.twitch.tv/kraken/channels/dmbrandon/subscriptions","editors":"https://api.twitch.tv/kraken/channels/dmbrandon/editors","videos":"https://api.twitch.tv/kraken/channels/dmbrandon/videos","teams":"https://api.twitch.tv/kraken/channels/dmbrandon/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/dmbrandon-channel_header_image-834c8de775823cf0-640x125.jpeg","display_name":"dmbrandon","game":"Smite","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/dmbrandon-profile_image-9b5af706b71a8b5d-300x300.jpeg","mature":false,"status":"Patch day :(","url":"http://www.twitch.tv/dmbrandon","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/dmbrandon-channel_offline_image-c95f92d3c078d790-640x360.jpeg","_id":4420730,"name":"dmbrandon","created_at":"2009-02-25T04:16:48Z","updated_at":"2014-08-20T04:33:38Z","abuse_reported":null,"delay":0,"followers":24899,"profile_banner":null,"profile_banner_background_color":null,"views":2323145,"language":"en"}},{"_id":10745559664,"game":"Modern Warfare 2","viewers":1620,"_links":{"self":"https://api.twitch.tv/kraken/streams/lolrenaynay"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_lolrenaynay-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_lolrenaynay-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_lolrenaynay-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_lolrenaynay-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/lolrenaynay","follows":"http://api.twitch.tv/kraken/channels/lolrenaynay/follows","commercial":"http://api.twitch.tv/kraken/channels/lolrenaynay/commercial","stream_key":"http://api.twitch.tv/kraken/channels/lolrenaynay/stream_key","chat":"http://api.twitch.tv/kraken/chat/lolrenaynay","features":"http://api.twitch.tv/kraken/channels/lolrenaynay/features","subscriptions":"http://api.twitch.tv/kraken/channels/lolrenaynay/subscriptions","editors":"http://api.twitch.tv/kraken/channels/lolrenaynay/editors","videos":"http://api.twitch.tv/kraken/channels/lolrenaynay/videos","teams":"http://api.twitch.tv/kraken/channels/lolrenaynay/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/lolrenaynay-channel_header_image-b993166411b9a97a-640x125.png","display_name":"lolRenaynay","game":"Modern Warfare 2","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/lolrenaynay-profile_image-37cb9beea8153225-300x300.jpeg","mature":true,"status":"Call of the Dudududududu  \u3064 \u25d5_\u25d5 \u3064 w/ Renaynay! (Xbox 360)","url":"http://www.twitch.tv/lolrenaynay","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/lolrenaynay-channel_offline_image-bc3b91ef17b018f4-640x360.png","_id":24522509,"name":"lolrenaynay","created_at":"2011-09-02T03:29:25Z","updated_at":"2014-08-20T04:43:41Z","abuse_reported":null,"delay":0,"followers":140317,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/lolrenaynay-profile_banner-f441c8253059de2f-480.jpeg","profile_banner_background_color":null,"views":4018309,"language":"en"}},{"_id":10745624944,"game":"Super Smash Bros. Melee","viewers":1558,"_links":{"self":"https://api.twitch.tv/kraken/streams/showdownsmash"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_showdownsmash-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_showdownsmash-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_showdownsmash-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_showdownsmash-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/showdownsmash","follows":"https://api.twitch.tv/kraken/channels/showdownsmash/follows","commercial":"https://api.twitch.tv/kraken/channels/showdownsmash/commercial","stream_key":"https://api.twitch.tv/kraken/channels/showdownsmash/stream_key","chat":"https://api.twitch.tv/kraken/chat/showdownsmash","features":"https://api.twitch.tv/kraken/channels/showdownsmash/features","subscriptions":"https://api.twitch.tv/kraken/channels/showdownsmash/subscriptions","editors":"https://api.twitch.tv/kraken/channels/showdownsmash/editors","videos":"https://api.twitch.tv/kraken/channels/showdownsmash/videos","teams":"https://api.twitch.tv/kraken/channels/showdownsmash/teams"},"background":null,"banner":null,"display_name":"ShowdownSmash","game":"Super Smash Bros. Melee","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/showdownsmash-profile_image-8dd8ec2011055dc5-300x300.png","mature":true,"status":"Get Smashed at the Foundry #13 - ft. PewPewU, Shroomed, Bizzarro Flame, Toph, SilentSpectre, L, Darrell, and more!","url":"http://www.twitch.tv/showdownsmash","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/showdownsmash-channel_offline_image-f9118d8aa082b92b-640x360.png","_id":59420086,"name":"showdownsmash","created_at":"2014-03-22T17:47:57Z","updated_at":"2014-08-20T02:23:22Z","abuse_reported":null,"delay":0,"followers":2049,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/showdownsmash-profile_banner-59e642b2a24c4979-480.png","profile_banner_background_color":"null","views":39898,"language":"en"}},{"_id":10746418496,"game":"League of Legends","viewers":1549,"_links":{"self":"https://api.twitch.tv/kraken/streams/espeonbot"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_espeonbot-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_espeonbot-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_espeonbot-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_espeonbot-{width}x{height}.jpg"},"channel":{"_links":{"self":"http://api.twitch.tv/kraken/channels/espeonbot","follows":"http://api.twitch.tv/kraken/channels/espeonbot/follows","commercial":"http://api.twitch.tv/kraken/channels/espeonbot/commercial","stream_key":"http://api.twitch.tv/kraken/channels/espeonbot/stream_key","chat":"http://api.twitch.tv/kraken/chat/espeonbot","features":"http://api.twitch.tv/kraken/channels/espeonbot/features","subscriptions":"http://api.twitch.tv/kraken/channels/espeonbot/subscriptions","editors":"http://api.twitch.tv/kraken/channels/espeonbot/editors","videos":"http://api.twitch.tv/kraken/channels/espeonbot/videos","teams":"http://api.twitch.tv/kraken/channels/espeonbot/teams"},"background":null,"banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/espeonbot-channel_header_image-2f3e5913b3fd9cad-640x125.png","display_name":"Espeonbot","game":"League of Legends","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/espeonbot-profile_image-aabe7f4bbfdc1d52-300x300.jpeg","mature":false,"status":"KaBuM Espeon - Suporte Challenger 750+ LP","url":"http://www.twitch.tv/espeonbot","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/espeonbot-channel_offline_image-9cc52b35fce5163b-640x360.png","_id":35946395,"name":"espeonbot","created_at":"2012-09-04T00:35:58Z","updated_at":"2014-08-20T03:27:25Z","abuse_reported":null,"delay":0,"followers":50396,"profile_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/espeonbot-profile_banner-f2e3f98dad6727b1-480.png","profile_banner_background_color":null,"views":3900627,"language":"en"}},{"_id":10747193664,"game":"NBA 2K14","viewers":1384,"_links":{"self":"https://api.twitch.tv/kraken/streams/chris_smoove"},"preview":{"small":"http://static-cdn.jtvnw.net/previews-ttv/live_user_chris_smoove-80x50.jpg","medium":"http://static-cdn.jtvnw.net/previews-ttv/live_user_chris_smoove-320x200.jpg","large":"http://static-cdn.jtvnw.net/previews-ttv/live_user_chris_smoove-640x400.jpg","template":"http://static-cdn.jtvnw.net/previews-ttv/live_user_chris_smoove-{width}x{height}.jpg"},"channel":{"_links":{"self":"https://api.twitch.tv/kraken/channels/chris_smoove","follows":"https://api.twitch.tv/kraken/channels/chris_smoove/follows","commercial":"https://api.twitch.tv/kraken/channels/chris_smoove/commercial","stream_key":"https://api.twitch.tv/kraken/channels/chris_smoove/stream_key","chat":"https://api.twitch.tv/kraken/chat/chris_smoove","features":"https://api.twitch.tv/kraken/channels/chris_smoove/features","subscriptions":"https://api.twitch.tv/kraken/channels/chris_smoove/subscriptions","editors":"https://api.twitch.tv/kraken/channels/chris_smoove/editors","videos":"https://api.twitch.tv/kraken/channels/chris_smoove/videos","teams":"https://api.twitch.tv/kraken/channels/chris_smoove/teams"},"background":null,"banner":null,"display_name":"Chris_Smoove","game":"NBA 2K14","logo":"http://static-cdn.jtvnw.net/jtv_user_pictures/chris_smoove-profile_image-e4f0fd13c7b2d866-300x300.jpeg","mature":false,"status":"End of Regular Season","url":"http://www.twitch.tv/chris_smoove","video_banner":"http://static-cdn.jtvnw.net/jtv_user_pictures/chris_smoove-channel_offline_image-47e7ff3f948e4d64-640x360.jpeg","_id":7382907,"name":"chris_smoove","created_at":"2009-07-25T00:22:01Z","updated_at":"2014-08-20T05:08:40Z","abuse_reported":null,"delay":0,"followers":36471,"profile_banner":null,"profile_banner_background_color":null,"views":1239376,"language":"en"}}],"_total":8971,"_links":{"self":"https://api.twitch.tv/kraken/streams?limit=25&offset=0","next":"https://api.twitch.tv/kraken/streams?limit=25&offset=25","featured":"https://api.twitch.tv/kraken/streams/featured","summary":"https://api.twitch.tv/kraken/streams/summary","followed":"https://api.twitch.tv/kraken/streams/followed"}}
```
```
@Trusty:~$ curl -s https://api.twitch.tv/kraken/streams | grep -o profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile
profile

```
```
@Trusty:~$ curl -s https://api.twitch.tv/kraken/streams | grep -c profile
1
```

---

### Post by steeldriver on 2014-08-20
> **dev18 said:**
> So any ideas how to make it work with a curl output?

> **dev18 said:**
> I wanting to be able to grep my way through this curl data to get even more specifics. 

You still haven't told us **what **you are trying to extract from the data - once you do that, we may be able to suggest something. For example, if you want to output all the quoted http or https URLS containing the word 'streams', you could do something like

```

$ curl -s https://api.twitch.tv/kraken/streams | grep -Eo '"https?:[^"]*streams[^"]*"'
"http://api.twitch.tv/kraken/streams/mushisgosu"
"http://api.twitch.tv/kraken/streams/amazhs"
"https://api.twitch.tv/kraken/streams/starladder1"
"https://api.twitch.tv/kraken/streams/reckful"
"https://api.twitch.tv/kraken/streams/sp4zie"
"https://api.twitch.tv/kraken/streams/dotastarladder_en"
"https://api.twitch.tv/kraken/streams/sirhcez"
"https://api.twitch.tv/kraken/streams/nightblue3"
"https://api.twitch.tv/kraken/streams/lightofheaven"
"https://api.twitch.tv/kraken/streams/joindotacommunity"
"https://api.twitch.tv/kraken/streams/nbk"
"http://api.twitch.tv/kraken/streams/manvsgame"
"https://api.twitch.tv/kraken/streams/tidesoftime"
"http://api.twitch.tv/kraken/streams/alexby11"
"https://api.twitch.tv/kraken/streams/asiagodtonegg3be0"
"http://api.twitch.tv/kraken/streams/flosd"
"https://api.twitch.tv/kraken/streams/topangatv"
"https://api.twitch.tv/kraken/streams/toyz_hkes"
"https://api.twitch.tv/kraken/streams/nervarien"
"https://api.twitch.tv/kraken/streams/m0e_tv"
"http://api.twitch.tv/kraken/streams/fishplaystreetfighter"
"https://api.twitch.tv/kraken/streams/garenatw"
"https://api.twitch.tv/kraken/streams/noxious_hs"
"https://api.twitch.tv/kraken/streams/smitegame"
"https://api.twitch.tv/kraken/streams/ceh9"
"https://api.twitch.tv/kraken/streams?limit=25&offset=0"
"https://api.twitch.tv/kraken/streams?limit=25&offset=25"
"https://api.twitch.tv/kraken/streams/featured"
"https://api.twitch.tv/kraken/streams/summary"
"https://api.twitch.tv/kraken/streams/followed"

```

---

### Post by dev18 on 2014-08-20
I knew writing the source to file was an option. Honestly, I didn't try because I didn't think it was practical for the overall application. As a single command it's fine, but in a loop, I don't know. Resource usage is top priority in my bash project because of the range of computers I want it to be able to run on. It's a background application so I though manipulating the source, as a string in memory, would have been more efficient.

   What steel posted is great! But I want to grab just one specific profile of my choice. Print it to the console. Then find the correlated that, that profile is playing. Print it to the console. Then I want to see how many viewers they currently have. Print it to the console. Then I want to grab and wget their profile picture and display it in ascii using jp2a. Print it to the console. Then And so on..... forever :D I'd prefer not to write anything to the disk, if that is an option.


Thanks guys for your advice so far.

---

### Post by steeldriver on 2014-08-20
it shouldn't matter how you provide the input to grep - you can save the curl output to a shell variable if you want
```

source="$(curl -s https://api.twitch.tv/kraken/streams)"

```
then either
```

echo "$source" | grep -Eo '"https?:[^"]*streams[^"]*"'

```
or (using a bash 'here string')
```

grep -Eo '"https?:[^"]*streams[^"]*"' <<< "$source"

```

---

### Post by dev18 on 2014-08-20
Yeah, I guess I still have much to learn steel. Working. :popcorn:


```
#!/bin/bash

clear
#GENERAL VARIABLES
confdir=$(pwd | sed 's/scripts//g') #config directory
logdir="$confdir"logs"" #logs directory
#

function featured() {
twkeywords=$(grep "twkeywords=" $confdir/config | sed 's/twkeywords=//g')
source=$(sudo curl -s https://api.twitch.tv/kraken/streams)
streams=$(echo "$source" | grep -Eo '"https?:[^"]*streams[^"]*"' | cut -d / -f 6 | tr '"' ' ' | head -n -5)



for i in ${twkeywords[@]}; do
    for x in ${streams[@]}; do    
        if [ "$i" == "$x" ]; then
            found="$found $i"
        fi
    done
clear
printf " $x = $i : $found"
done

found=""

}
featured

```

---

### Post by Vaphell on 2014-08-21
by accident if anything

```
for i in ${twkeywords[@]}; do
    for x in ${streams[@]}; do
```

this piece calls 2 arrays...

```
twkeywords=$(grep "twkeywords=" $confdir/config | sed 's/twkeywords=//g')
streams=$(echo "$source" | grep -Eo '"https?:[^"]*streams[^"]*"' | cut -d / -f 6 | tr '"' ' ' | head -n -5)
```

... but these variables are not arrays

---

### Post by dev18 on 2014-08-21
> **Vaphell said:**
> by accident if anything

```
for i in ${twkeywords[@]}; do
    for x in ${streams[@]}; do
```

this piece calls 2 arrays...

```
twkeywords=$(grep "twkeywords=" $confdir/config | sed 's/twkeywords=//g')
streams=$(echo "$source" | grep -Eo '"https?:[^"]*streams[^"]*"' | cut -d / -f 6 | tr '"' ' ' | head -n -5)
```

... but these variables are not arrays

At this point of my knowledge of Bash, I couldn't tell ya'. Especially when talking about arrays in Bash. Their definitely not declared :D. But hey, it works and I'm just poking around testing things. 

In this case:
$twkeywords=giantwaffle lirik swiftor cohcarnage dansgaming summit1g day9tv manvsgame ezekiel_iii. I don't want to announce all the top streams, just the ones I follow. Which is listed in a config file, something like a following list. If you copy pasta, it wouldn't work.

$streams=
roomonfire 
joindotared 
nightblue3 
imaqtpie 
lirik 
reckful 
ceh9 
flosd 
gsstudio_dota 
forsenlol 
ihearthusite 
sevadus 
oxichampion 
manvsgame 
timthetatman 
kolento 
starladder1 
riotgames 
quickybaby 
debitorlp 
mdstephano 
lightofheaven 
fishplaystreetfighter 
sethbling 
diablo 

They have the same format or style, so I thought that array command would do.

---

### Post by Vaphell on 2014-08-21
```
#!/bin/bash

readarray -t streams < <( curl -s https://api.twitch.tv/kraken/streams \
                          | grep -Eo 'https?:[^"]*streams[^"]*' \
                          | awk -F/ '{ print $NF; }' \
                          | grep -Ff streams.list )

printf 'stream "%s" found\n' "${streams[@]}"
```

```
$ cat streams.list
giantwaffle
lirik
swiftor
cohcarnage
dansgaming
summit1g
day9tv
manvsgame
ezekiel_iii
$ ./streams.bash
stream "day9tv" found
stream "swiftor" found
stream "dansgaming" found
```

---

### Post by Vaphell on 2014-08-21
triple post due to killer lag

---

### Post by Vaphell on 2014-08-21
triple post due to killer lag

---

### Post by dev18 on 2014-08-23
> **Vaphell said:**
> ```
#!/bin/bash

readarray -t streams < <( curl -s https://api.twitch.tv/kraken/streams \
                          | grep -Eo 'https?:[^"]*streams[^"]*' \
                          | awk -F/ '{ print $NF; }' \
                          | grep -Ff streams.list )

printf 'stream "%s" found\n' "${streams[@]}"
```


Thanks vaphell. I had no idea there was even a readarray command. Also I know of <, and <<, and <<<, but not < <(). Is that the syntax to inject a function into a read command or something else?

---

### Post by Vaphell on 2014-08-23
readarray is a bash way to create arrays from inputs on per line basis. I assume it was introduced because it is a relatively common use case even though the same thing should be possible with a bit more convoluted *read* or with a *while read* loop.
```
$ IFS=$'\n' read -rd '' -a arr <<< $'a a a\nb b b\nc c c\n'
$ printf '[%s]\n' "${arr[@]}"
[a a a]
[b b b]
[c c c]
$ arr=()
$ while read -r ln; do arr+=( "$ln" ); done <<< $'a a a\nb b b\nc c c\n'
$ printf '[%s]\n' "${arr[@]}"
[a a a]
[b b b]
[c c c]
[]
```
there are some differences in how the empty lines are treated though.

< <() is 2 separate features in reality, that's why the space between <'s is important
first part is the standard redirection from a file <, the other is called a process substitution - it takes a cmd output and makes a pseudofile out of it. Whenever a file param is expected, you can use <(...) there.

```
$ grep -f [COLOR="#0000FF"]<( echo bcd )[/COLOR] <<< "abcdef"
a**[COLOR="#FF0000"]bcd[/COLOR]**ef
```

there is also version in the other direction: > >(...), eg used with exec to pass all script outputs through some program.

---

### Post by dev18 on 2014-08-23
> **Vaphell said:**
> readarray is a bash way to create arrays from inputs on per line basis. I assume it was introduced because it is a relatively common use case even though the same thing should be possible with a bit more convoluted *read* or with a *while read* loop.
```
$ IFS=$'\n' read -rd '' -a arr <<< $'a a a\nb b b\nc c c\n'
$ printf '[%s]\n' "${arr[@]}"
[a a a]
[b b b]
[c c c]
$ arr=()
$ while read -r ln; do arr+=( "$ln" ); done <<< $'a a a\nb b b\nc c c\n'
$ printf '[%s]\n' "${arr[@]}"
[a a a]
[b b b]
[c c c]
[]
```
there are some differences in how the empty lines are treated though.

< <() is 2 separate features in reality, that's why the space between <'s is important
first part is the standard redirection from a file <, the other is called a process substitution - it takes a cmd output and makes a pseudofile out of it. Whenever a file param is expected, you can use <(...) there.

```
$ grep -f [COLOR=#0000FF]<( echo bcd )[/COLOR] <<< "abcdef"
a**[COLOR=#FF0000]bcd[/COLOR]**ef
```

there is also version in the other direction: > >(...), eg used with exec to pass all script outputs through some program.

Gotcha! Thank you so much so a understandable explanation! Just when you thought you had a slight understanding of something... redirection. Mind blown ;).

---

