---
title: "Bash. Voice Notification"
date: 2014-10-30
forum: Programming Talk
---

### Post by dcc0 on 2014-10-30
I created a small script: It checks the availability of ip or site and it notifies with the voice when it's up or down. It works like daemon. It notifies for one time if the status of a source has changed. The idea: to make a voice notification script. 
I will be very glad if it will be useful for somebody.  And if somebody will make it better I will greet it.
I tried to make a binary with the SHC, to test is that better than original. Maybe I have posted the first message not in the right place. And it was a mistake to post links to binary and c# source. I will be glad if somebody compile it with the SHC and tests on x86.Thank you. 
Dear moderators this message is not a spam. And I am a real linux user, just user.
 **About script:**
 It's is bash (good or not - I am not a professional programmer)
It depends **on festival** packet. 



> #!/bin/bash
clear
ip=0
count=1
prev_is_site_up=0
cur_is_site_up=0


read_ip() {
echo -n "Enter site IP:"
 read ip
# TODO: add some IP address validation here
}
 
# Returns 1 if site is up, 0 &#8212; site is down
test_site() {
res=$(ping -c ${count} ${ip} | tail -2 | head -1 | awk '{print $4}') 2> /dev/null

if [ "$res" = $count ]; then

 return 1
  
   else

 return 0
fi;

}
 
notify() {

if [ $prev_is_site_up -eq 1 ]; then

echo "It is up" | festival --tts

  else

echo "It is down" | festival --tts
fi
}
 
script_init() {

test_site

 prev_is_site_up=$?

notify
}
 
script_loop() {

while :; do
 
 sleep 5
test_site

cur_is_site_up=$?
 
 if [ $cur_is_site_up -ne $prev_is_site_up ]; then

 prev_is_site_up=$cur_is_site_up
notify
fi
done

}


read_ip
script_init
script_loop

---

### Post by Habitual on 2014-10-30
I suggest not to use ping as a test.
ICMP packets could be dropped, so it's not reliable as a test.
I've used ```
curl -Is [http://xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx) | \grep -E '^Server' | cut -c9-21
``` in another script I wrote to 'check' for the daemon package running the site.

Example: mbe.com is running IIS
```
curl -Is http://mbe.com  | \grep -E '^Server' | cut -c9-21
```

ubuntuforums.org seems to be running apache/2.2.22
```
curl -Is http://ubuntuforums.org  | \grep -E '^Server' | cut -c9-21
```

Just a thought.

---

