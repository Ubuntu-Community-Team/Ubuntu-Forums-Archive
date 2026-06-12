---
title: "Fun things"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by hypnot0ad on 2012-06-29
Hello, this isn't really a technical question, but I was wondering what are some fun things for people who are  new to Ubuntu to do.

Like things to get us comfortable with the terminal/system.
Things like that.

tyvm.

---

### Post by cryptotheslow on 2012-06-29
Really depends on what you find fun :D

For silly value:
```
sudo apt-get moo
```

Spoiler on what it does and other nonsense here:
[http://superuser.com/questions/119397/sudo-apt-get-moo-and-other-easter-eggs-in-linux](http://superuser.com/questions/119397/sudo-apt-get-moo-and-other-easter-eggs-in-linux)

---

### Post by papibe on 2012-06-29
Hi hypnot0ad. Welcome to the forums!

I would recommend to  challenge yourself with "real" projects (or a learning projects if you will). For example:
[LIST]
[*]Share files with Windows machines.
[*]Enable remote access to your computer
[*]Stream media to a game console.
[*]Share your printer with other machines.
[*]Setup remote access to your files from the Internet.
[*]etc.
[/LIST]
Another approach would be to learn how to do things you do before (in Windows or Mac?):
[LIST]
[*]Setup your IM accounts in Empathy (or Pidgin).
[*]Setup all your email accounts in Thunderbird.
[*]Install and test Skype.
[*]Use LibreOffice to create and modify some files.
[*]Use Openshot to create  presentation and movies (like iMove or Windows Movie Maker).
[*]Rip CDs to mp3s (or flac, or ogg, etc).
[*]etc.
[/LIST]
Just some thoughts. Come here often, and tell us how it goes.
Regards.

---

### Post by sudodus on 2012-06-29
This link will give you a lot to read and test about command line stuff
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1909108_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1909108")

---

### Post by hypnot0ad on 2012-06-29
wow thanks.

@[[COLOR=#DD4814]**papibe**[/COLOR]]("http://ubuntuforums.org/member.php?u=774785"):
I will go a head and do most of those. They are great ideas, and a really good place to start. Looking forward to staying and learning/teaching.

@[sudodus]("http://ubuntuforums.org/member.php?u=1499021"):
Thank you I have seen that link and will be busy for some time now because of it.


Love the moo.

---

### Post by jllipke on 2012-06-29
> Getting Install packages by using 
```
sudo apt-get install "whatever u need"
```         instead of using software center gets u used to the terminal
         
          > Simply Searching the web
          > Remote Desktop use
          > Using MyUnity for system themes and tweaks to get used to the UI
          > Creating Projects with Libre Office
          > Learning Terminal commands for future use

These are the usual for me :)

---

### Post by Mopar1973Man on 2012-06-29
> **papibe said:**
> Hi hypnot0ad. Welcome to the forums!

I would recommend to  challenge yourself with "real" projects (or a learning projects if you will). For example:
[LIST]
[*]Share files with Windows machines.
[*]Enable remote access to your computer
[*]Stream media to a game console.
[*]Share your printer with other machines.
[*]Setup remote access to your files from the Internet.
[*]etc.
[/LIST]
Another approach would be to learn how to do things you do before (in Windows or Mac?):
[LIST]
[*]Setup your IM accounts in Empathy (or Pidgin).
[*]Setup all your email accounts in Thunderbird.
[*]Install and test Skype.
[*]Use LibreOffice to create and modify some files.
[*]Use Openshot to create  presentation and movies (like iMove or Windows Movie Maker).
[*]Rip CDs to mp3s (or flac, or ogg, etc).
[*]etc.
[/LIST]
Just some thoughts. Come here often, and tell us how it goes.
Regards.

He's right. But be patient! Do your study work and read up on how to do it properly.  I've spent a bunch of time being frustrated and kept giving up and going back to Windows because it was easier to get the work done. But if you allow yourself time and time ahead to future computer job you got to do... Go study up and enjoy learning about Linux...  ;)

---

### Post by hypnot0ad on 2012-06-29
> **jllipke said:**
> > Getting Install packages by using 
```
sudo apt-get install "whatever u need"
```         instead of using software center gets u used to the terminal
         
          > Simply Searching the web
          > Remote Desktop use
          > Using MyUnity for system themes and tweaks to get used to the UI
          > Creating Projects with Libre Office
          > Learning Terminal commands for future use

These are the usual for me :)

When ever I do:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update

``` I get:
```
E: Unable to locate package update

```I've spent about the last hour and half looking through this site trying to find a solution but am to no avail.

---

### Post by hypnot0ad on 2012-06-29
> **Mopar1973Man said:**
> But if you allow yourself time and time ahead to future computer job you got to do... Go study up and enjoy learning about Linux...  ;)

Thats why I'm here :D

---

### Post by papibe on 2012-06-29
Could you post the complete command you are trying to run, and its results?

Regards.

---

### Post by jllipke on 2012-06-29
> **hypnot0ad said:**
> When ever I do:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update

``` I get:
```
E: Unable to locate package update

```I've spent about the last hour and half looking through this site trying to find a solution but am to no avail.

well, maybe it is not the correct name of the package. One day I wanted to install lm-sensors, I typed it in as ```
sudo apt-get lm sensors
``` ( notice the space between lm and sensors ) and it came up with ```
lm: command not found
``` I was supposed to put a dash between lm and sensors. I'm sayin the slightest screw up could alter your results

---

### Post by hypnot0ad on 2012-06-29
> **papibe said:**
> Could you post the complete command you are trying to run, and its results?

Regards.

```
fangrat@DX-3-2814:~$ sudo apt-get install update
[sudo] Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
fangrat@DX-3-2814:~$ 

```

---

### Post by papibe on 2012-06-29
The command for update the repositories is:
```
sudo apt-get update
```

The command to install lm-sensors:
```
sudo apt-get install lm-sensors 
```

Tell us how it goes.
Regards.

---

### Post by hypnot0ad on 2012-06-29
> **papibe said:**
> The command for update the repositories is:
```
sudo apt-get update
```The command to install lm-sensors:
```
sudo apt-get install lm-sensors 
```Tell us how it goes.
Regards.

Everything works until I do the last install update.
I get the same message.

What are the lm-sensors?
jw

---

### Post by jmfal on 2012-06-29
Welcome to  Ubuntu

Try removing the hyphen after "lm"

Another fun thing is to build your own "conky"

---

### Post by hypnot0ad on 2012-06-29
> **jmfal said:**
> Welcome to  Ubuntu

Try removing the hyphen after "lm"

Another fun thing is to build your own "conky"

Like this?

```
fangrat@DX-3-2814:~$ sudo apt-get lm sensors
[sudo] password for fangrat: 
E: Invalid operation lm
fangrat@DX-3-2814:~$ 

```

What do you mean by "conky?"

---

### Post by jmfal on 2012-06-29
Paste this into the terminal

```
 sudo apt-get install lm-sensors      
```


google conky  and in the forum cafe section of the forum is the great conky thread, its about 2000 pages and has over 10,000 posts its a hard ware monitor that uses the lm-sensors and more , calanders etc., you'll see just look at the screenshots

---

### Post by hypnot0ad on 2012-06-30
> **jmfal said:**
> Paste this into the terminal

```
 sudo apt-get install lm-sensors      
```google conky  and in the forum cafe section of the forum is the great conky thread, its about 2000 pages and has over 10,000 posts its a hard ware monitor that uses the lm-sensors and more , calanders etc., you'll see just look at the screenshots


Okay.

```
fangrat@DX-3-2814:~$ sudo apt-get install lm-sensors
[sudo] password for fangrat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fangrat@DX-3-2814:~$ 

```and I still get the same result after typing "sudo apt-get install.."

---

### Post by sudodus on 2012-06-30
> **hypnot0ad said:**
> Okay.

```
fangrat@DX-3-2814:~$ sudo apt-get install lm-sensors
[sudo] password for fangrat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fangrat@DX-3-2814:~$ 

```and I still get the same result after typing "sudo apt-get install.."
This means that lm-sensors is already installed and the newest version, so it is saying 'everything is fine with lm-sensors'.

---

### Post by Nytram on 2012-06-30
Recently I setup a simple script along with keyboard shortcuts so that when I launch an app the name of it is spoken aloud, it's useful because it gives me feedback that I've hit the right key combo. Fun too, at least I think so 8)

---

