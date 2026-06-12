---
title: "BASH: Parse Youtube video id?"
date: 2012-04-27
forum: Programming Talk
---

### Post by ICDeadPpl on 2012-04-27
I'd like some help with a bash script, which sends a RPC call to XBMC with a Youtube video id.

As it is now, it works it the URL is like this:
http://www.youtube.com/watch?v=KyCYyoGusqs

It won't work if it looks like this:
http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs

Could someone show how to parse the "v" value of the URL, no matter what's in the URL?

```
#!/bin/bash

if [ "$1" = "" ]; then
	echo -n "Insert Youtube URL: "
	read url
else
	url="$1"
fi

myVideo=$(echo $url | awk -F "v=" '{print $2}')
#echo "VideoID: "$myVideo

wget --user=xbmc --password=password --delete-after --header='Content-Type: application/json' --post-data='{"jsonrpc": "2.0", "method": "Player.Open", "params":{"item": {"file" : "plugin://plugin.video.youtube/?action=play_video&videoid='$myVideo'" }}, "id" : "1"}' http://192.168.0.10:8082/jsonrpc

```

---

### Post by papibe on 2012-04-27
Hi ICDeadPpl. Welcome to the forums!

I would use the bash parameter substitution. For instance:
```
$ url="http://www.youtube.com/watch?v=KyCYyoGusqs"
$ echo "$url"
http://www.youtube.com/watch?v=KyCYyoGusqs

$ echo "${url#*v=}"
KyCYyoGusqs
```
Here you have a good [tutorial]("http://linuxgazette.net/18/bash.html") for that functionality.

I hope that helps and tell us how it goes.
Regards.

---

### Post by ICDeadPpl on 2012-04-27
```
With this code it works:


#!/bin/bash

echo -n "Insert Youtube URL: "
read url
echo "URL: "$url

myVideo="${url#*v=}"
echo "VideoID: "$myVideo

wget --user=jrock --password=lonkero01 --delete-after --header='Content-Type: application/json' --post-data='{"jsonrpc": "2.0", "method": "Player.Open", "params":{"item": {"file" : "plugin://plugin.video.youtube/?action=play_video&videoid='$myVideo'" }}, "id" : "1"}' http://192.168.0.10:8082/jsonrpc

```

What I don't understand is that why it doesn't work if I want to pass the Youtube URL as an argument?

If I pass the URL as argument "$1", the parsing won't work, but if I read the URL from the "read" statement it works.

I removed the 'if [ "$1" = "" ]; then' segment from the original version as you can see, but it means I can't automate submitting URLs to the script.
Any clues as how to solve that the script works with passing the URL as an argument?

Edit: The URL usually looks like this: [http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs](http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs)
Note the "feature=player_embedded&" section, which has to be ignored. There sometimes are other extra "parts" in a Youtube URL as well...

---

### Post by Vaphell on 2012-04-27
```
$ echo "http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s
> http://www.youtube.com/watch?v=KyCYyoGusqs#t=11m5s
> http://www.youtube.com/watch?v=KyCYyoGusqs"

http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s
http://www.youtube.com/watch?v=KyCYyoGusqs#t=11m5s
http://www.youtube.com/watch?v=KyCYyoGusqs


$ echo "http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s
http://www.youtube.com/watch?v=KyCYyoGusqs#t=11m5s
http://www.youtube.com/watch?v=KyCYyoGusqs" | sed -r 's/^.*[&?]v=(.{11})([&#].*)?$/\1/'

KyCYyoGusqs
KyCYyoGusqs
KyCYyoGusqs
```

---

### Post by ofnuts on 2012-04-27
```
myVideo=$(echo $url | tr "?&" "\n\n" | grep "^v=" | cut -d "=" -f 2)
```In slow motion:
- put every parameter  of the URL on its own line by changing "&" and "?" into newlines
- keep the line starting  with "v="
- cut on "=" and keep the second  field

---

### Post by ICDeadPpl on 2012-04-27
Thanks for the help so far!

Now the only "problem" is that I have to enclose the URL in double quotes when running the script, like this:

[Example 1]
```
$ yt2xbmc "http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s"

Output:

URL: "http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s"
VideoID: KyCYyoGusqs#t
```

When I don't use double quotes it looks like this:

[Example 2]
```
$ yt2xbmc.sh http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s
[2] 12390
$ URL: "http://www.youtube.com/watch?feature=player_embedded"
VideoID: 

[2]-  Done                    yt2xbmc.sh http://www.youtube.com/watch?feature=player_embedded

```

The script so far:

```
#!/bin/bash

if [ "$1" = "" ]; then
      echo -n "Insert Youtube URL: "
      read url
else
      url="$1"
fi
echo URL: $url

myVideo=$(echo "$url" | tr "?&" "\n\n" | grep -re "^v=" | cut -d "=" -f 2)
echo "VideoID: "$myVideo

#wget --user=xbmc --password=password --delete-after --header='Content-Type: application/json' --post-data='{"jsonrpc": "2.0", "method": "Player.Open", "params":{"item": {"file" : "plugin://plugin.video.youtube/?action=play_video&videoid='$myVideo'" }}, "id" : "1"}' http://192.168.0.10:8082/jsonrpc

```


Somehow it prints the $url as "http://www.youtube.com/watch?feature=player_embedded", omitting everything after 'feature=player_embedded', strange?

Is the some kind of "padding" or some escape characters needed for the "$1" in the script when submitting the URL without double quotes?

BTW, the extra "#t" characters at the end of VideoID in Example 1 are not part of the video id, but Youtube seems to ignore those. The URL submitted to XBMC works fine with those characters.

---

### Post by ofnuts on 2012-04-27
> **ICDeadPpl said:**
> Thanks for the help so far!

Now the only "problem" is that I have to enclose the URL in double quotes when running the script, like this:

[Example 1]
```
$ yt2xbmc "http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s"

Output:

URL: "http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s"
VideoID: KyCYyoGusqs#t
```When I don't use double quotes it looks like this:

[Example 2]
```
$ yt2xbmc.sh http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s
[2] 12390
$ URL: "http://www.youtube.com/watch?feature=player_embedded"
VideoID: 

[2]-  Done                    yt2xbmc.sh http://www.youtube.com/watch?feature=player_embedded

```The script so far:

```
#!/bin/bash

if [ "$1" = "" ]; then
      echo -n "Insert Youtube URL: "
      read url
else
      url="$1"
fi
echo URL: $url

myVideo=$(echo "$url" | tr "?&" "\n\n" | grep -re "^v=" | cut -d "=" -f 2)
echo "VideoID: "$myVideo

#wget --user=xbmc --password=password --delete-after --header='Content-Type: application/json' --post-data='{"jsonrpc": "2.0", "method": "Player.Open", "params":{"item": {"file" : "plugin://plugin.video.youtube/?action=play_video&videoid='$myVideo'" }}, "id" : "1"}' http://192.168.0.10:8082/jsonrpc

```
Somehow it prints the $url as "http://www.youtube.com/watch?feature=player_embedded", omitting everything after 'feature=player_embedded', strange?

Is the some kind of "padding" or some escape characters needed for the "$1" in the script when submitting the URL without double quotes?

BTW, the extra "#t" characters at the end of VideoID in Example 1 are not part of the video id, but Youtube seems to ignore those. The URL submitted to XBMC works fine with those characters.
Outside of double quotes "&" has a meaning for the shell. Everything on the left is used as a command started in background and execution continues with stuff on the right (assuming it can be executed).

---

### Post by Vaphell on 2012-04-27
you have to quote or escape &

& is used at the end of command to run it without waiting for it to end, it's like an asynchronous version of ;


btw, video id gets polluted by part of the timestamp (#t=XmY)
> Output:

URL: "http://www.youtube.com/watch?feature=player_embedded&v=KyCYyoGusqs#t=11m5s"
VideoID: KyCYyoGusqs**#t**
you need to tweak your code, probably add # to tr
additionally you can take advantage of the fact that the id is always 11 chars long, but it's not necessary
```
grep -E '^v=.{11}$'
```

---

### Post by ICDeadPpl on 2012-04-28
Thanks!
Now it works and it's "clean" too, regarding the timestamp value!

```
myVideo=$(echo "$url" | tr "?&#" "\n\n" | grep -re "^v=" | cut -d "=" -f 2)
```

Happy camper!

---

