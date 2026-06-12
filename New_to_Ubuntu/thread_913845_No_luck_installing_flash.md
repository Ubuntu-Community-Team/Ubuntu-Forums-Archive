---
title: "No luck installing flash"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Dr Noam on 2008-09-08
Hi, I've had no luck installing flash player on my wubi-downloaded ubuntu despite advice from several people, and don't know what the problem is. I've tried using the restricted repository and installing flash plugin
nonfree, but that made no difference. Using the synaptic package manager, I got an error message told me I needed the ubuntu CD/DVD.

Can someone tell me:
Is installing flash always this difficult with linux?
Is there another way to view youtube and other videos online, or other applications using flash that might be easier?

Thanks,
Noam

---

### Post by szymon_g on 2008-09-08
is it x32 or x64 bit system (amd64, core2duo)?

---

### Post by Dr Noam on 2008-09-08
I think it's a 64-bit. Remind me how I can tell? :oops:

---

### Post by Marshal0505 on 2008-09-08
> **Dr Noam said:**
> I think it's a 64-bit. Remind me how I can tell? :oops:

```
uname -a
```

watch for x86 or x86_64

next time you forget you can try 
```
man uname
```
saves you from having to memorize everything ;)

---

### Post by Dr Noam on 2008-09-08
Thanks, x86_64, so 64 bit.

---

### Post by starcannon on 2008-09-08
Open up 

System>Administration>Software Sources 

uncheck the box for the CD media at the bottom of the window.
Close the window, and let it reload.

[strike]then if your running 32bit
```
sudo apt-get install ubuntu-restricted-extras
```[/strike]

there is likely a similarly named package for x64bit version, open up:

System>Administration>Synaptic Package Manager

search: ubuntu-restricted-extras

put a check next to it, apply, apply again, enjoy.

This'll put flash, java, and a bunch of other handy codecs, and media extra's on there for you; all in one wallop.

GL have fun.

---

### Post by szymon_g on 2008-09-08
ok, thats the way it worked for me

1.
sudo aptitude install ia32-libs ia32-libs-gtk linux32 lib32asound2 nspluginwrapper gsfonts-x11

2.
wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

3.
turning off mozilla firefox

4.
unpack downloaded file to Desktop

5.
cd Desktop/install_flash_player_9_linux

6.
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

7.
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

8.
cp libflashplayer.so $HOME/.mozilla/firefox/plugins/

9.
nspluginwrapper -i $HOME/.mozilla/firefox/plugins/libflashplayer.so

TA-DA!!!

ps. $HOME is your home directory (usually /home/my_user_name/).
i'm also a but unsure about plugins directory- you have to find it yourself (in your home directory). i dont have ubuntu now, so i cannot be sure :>

---

### Post by Dr Noam on 2008-09-08
Sorry Starcannon, tried all of that, no change.

I'll try Szymon's way. 

PS Is there an easy way to cut and paste to the terminal? I have one arm in a sling at the mo, and am typing very slowly...

---

### Post by Dougie187 on 2008-09-08
You can just highlight something and middle click. That will paste it.

The highlighting is essentially copy
Also, you can use Ctrl+Insert or Shift+Insert.

I think they are found in the edit menu of the terminal.

---

### Post by Dr Noam on 2008-09-08
OK I managed as far as here:

> **szymon_g said:**
> ...
9. nspluginwrapper -i $HOME/.mozilla/firefox/plugins/libflashplayer.so
...

Then I got:
nspluginwrapper: /home/noam/.mozilla/firefox/plugins/libflashplayer.so is not a valid NPAPI plugin

Any thoughts? Thanks.

---

### Post by Dougie187 on 2008-09-08
I'm not sure if this is the issue, but it could potentially be wubi. I have heard a lot of people having issues with wubi, and from what I have heard, noone really recommends it for actual use. Just for a bit of testing to see if it's worth the time to install it dual boot. I don't know though, someone might recommend it for actual use, but personally I would say only use it for a while, then if you like ubuntu, set up a dual boot if you need windows still.

In a fresh installation of ubuntu though, installing the flash plugin is usually cake. I mean even firefox has it as an addon, so you can just go to a flash site and click get missing plugins.

---

### Post by Dr Noam on 2008-09-08
I take your point Dougie, and I previously tried the direct download approach unsuccessfully. Don't know what else to try - flashblock is off. I could try re-installing wubi, that would be a pain, though. Also, I see a new thread emerging here...

---

### Post by Dr Noam on 2008-09-08
Might other things like gnash and non-free be getting in the way?

[edit:] Yep, removing gnash and following the instructions in this thread [http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490") I can now waste my time on youtube...

---

### Post by Dougie187 on 2008-09-08
Glad to hear it got solved. Please mark your thread as solved.

---

