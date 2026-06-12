---
title: "Flash Problems"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by katya_sehgal on 2011-12-05
From surfing the threads, I have got that.

Adobe is not friendly with Unix.
This is a long-standing problem. 
That the global storage options don't work.
That there are already reported bugs in launchpad.
HTML5 will take time.
Lightspark and HTML5 are not everywhere.

If there are solved threads, kindly point them out.

I am certain there must be a work-around.

---

### Post by katya_sehgal on 2011-12-06
After reading the internet, I have found that Flash is a long-standing issue of contention. Since 2009, Ubuntu user have problems in using Flash for video chat. If the program asks you if you want to allow video chat (always recommended), then you will have no option to either click on 'yes' or 'no'.

In addition, if you right-click when a video is playing..

... and select 'Settings', the small window that opens is 'non-clickable'. You have no other option than to reload the page. On youtube, this problem can be temporarily averted by using HTML5.
This was mentioned by cbowman57:

> If your primary use of Flash is for things like Youtube videos you may want to opt in for HTML5 trial [http://www.youtube.com/html5](http://www.youtube.com/html5) , if it works for you it's better than flash.


However, not all sites are compatible with HTML5. Or Lightspark, an open source alternative.

**Solutions?**
Some users have changed the 'Global Storage' settings. That is, right click when a video is playing (for sites using Flash) and then select 'Global Settings'. A new tab opens wherein you can increase your Global Storage settings (say, from 10kb to 1 mb). Basically allowing the sites to store information on your laptop. This worked for a few. Not the plentiful others.

I learned from another forum that Flash is unable to access the .adobe and .macromedia files in the Home directory of Ubuntu. Which is why the problems persist. As a solution, you may delete these folders and Flash will set it up again. This worked for some. Not the plentiful others.

As an option, it was recommended that you right-click on .adobe and .macromedia and change the permissions to 'Read and Write'. I am unable to do that like many others (shall post link if found).

I am not sure if this solution will work. However, would it be possible to change the permissions of these 2 folders. Every time I make a change, it accepts, but immediately reverts to the older settings.

I am certain that the experienced members have found a work-around. Otherwise how would they use the Flash services?

I would be glad for a solution. 
Cheers.

[SIZE="2"][SIZE="1"]P.S: From Adobe Forum (old but applicable)[/SIZE][/SIZE]

```
http://forums.adobe.com/thread/24111

```

---

### Post by Bodsda on 2011-12-06
Flash works fine for me....

Haven't installed it recently, but it used to be something like

```

sudo apt-get install flashplugin-nonfree

```

---

### Post by katya_sehgal on 2011-12-06
> **Bodsda said:**
> Flash works fine for me....

Haven't installed it recently, but it used to be something like

```

sudo apt-get install flashplugin-nonfree

```

Hello Bodsda. This is what I have done. I [COLOR="Navy"]uninstalled Flash[/COLOR] from the Software Centre and [COLOR="navy"]re installed[/COLOR] it. No result.

A google search of 

> sudo apt-get install flashplugin-nonfree


brought me to this forum in which a user named kerry_s wrote:


> use "flashplugin-installer", better yet just install "ubuntu-restricted-extras" & get everything you need on the first go.
.

Which was my original plan [**[COLOR="Navy"]in this thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1891208") (from where I have been transferred)

I shall now use your code.
However, [COLOR="navy"]should I first uninstall Flash from Software Centre[/COLOR] to prevent any crash?

---

### Post by Paqman on 2011-12-06
> **katya_sehgal said:**
> 
However, [COLOR="navy"]should I first uninstall Flash from Software Centre[/COLOR] to prevent any crash?

No need. You already have Flash.

The correct package for Flash these days is flashplugin-installer, which is also contained within ubuntu-restricted-extras. Installing either of these will give you Flash.

Can you be a bit more specific about what exact problem you're having? Is there a particular website that is not working correctly for you?

---

### Post by Frogs Hair on 2011-12-06
Flash works well for me since 9.10 with both Firefox and Opera . Global storage doesn't seem to affect the ability to view flash content because they are set to default.
 
locally shared objects are removed by an add-on when the browser is closed . I am only viewing content , not downloading and saving it for my own use later , so I don't know if that is a factor or not . I also use the Flash Aid add-on for Firefox to install the latest version of flash .

---

### Post by katya_sehgal on 2011-12-06
> **Paqman said:**
> No need. You already have Flash.

The correct package for Flash these days is flashplugin-installer, which is also contained within ubuntu-restricted-extras. Installing either of these will give you Flash.

Can you be a bit more specific about what exact problem you're having? Is there a particular website that is not working correctly for you?

Any service that asks your permission to switch on mic or/and camera. That includes _all browser based chatting services_. It includes Firefox and Chrome.

YouTube. I am using HTML5 on YouTube in Chrome. In Firefox, on Flash, this is what happens. 


1.```
 http://tinypic.com/view.php?pic=21eyy6w&s=5 
```
Right-clicking - settings - Adobe Flash Player Settings Box. 
The box you see in the image is non-clickable. This is repeated on any website using Flash.

Take any popular chat room. For instance:

```
http://tinypic.com/view.php?pic=zm1hk2&s=5

```

Certainly the service would ask you permission before switching on the webcam. When that happens, the Adobe Flash Player Settings box reappears and - like in YouTube - makes it impossible to proceed.

Another example

```
http://tinypic.com/view.php?pic=11tr8du&s=5
```
The Adobe Flash Player settings box acts like a villain. 

This is repeated for some medical and philosophy sites (any site really). But I think this would clear the picture.

Here is an Adobe Forum from 2009 stating the same issue. 
```
http://forums.adobe.com/thread/24111
```

If this is not clear, I will try again to make it clear. Just let me know.

---

### Post by katya_sehgal on 2011-12-06
For your understanding...

Results after entering:

> sudo apt-get install flashplugin-nonfree


> anil@anil-Inspiron-1420:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for anil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flashplugin-downloader' instead of 'flashplugin-nonfree'
flashplugin-downloader is already the newest version.
flashplugin-downloader set to manually installed.
The following package was automatically installed and is no longer required:
  linux-headers-3.0.0-12-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
anil@anil-Inspiron-1420:~$

---

### Post by pqwoerituytrueiwoq on 2011-12-06
aside from adobe flash occasionally freezing my computer (when i close a page with flash videos on it) i have not had any issues with it

if you are trying to play videos pause the video and run this command
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem /tmp/"movie-$d"
```

---

### Post by katya_sehgal on 2011-12-07
> **pqwoerituytrueiwoq said:**
> aside from adobe flash occasionally freezing my computer (when i close a page with flash videos on it) i have not had any issues with it

if you are trying to play videos pause the video and run this command
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem /tmp/"movie-$d"
```

Hello pqwoerituytrueiwoq.
If I run into this problem, I shall surely run your command in the terminal.
My issue is different.
Do check the above post relating to adobe Flash Player Settings.
Would you know of a solution?

---

### Post by dBuster on 2011-12-07
Slightly different problem for me.

Ubuntu 10.04.02 64 bit
64 bit flash both current and the beta from flashaid

With the beta I can't even view videos on youtube

other websites throw me an error 2046 or error 2032...

Can't seem to get around that.  Been told to upgrade but I am waiting for 12.04 before thinking of that.  Errors occur in any web browser I try.

---

### Post by katya_sehgal on 2011-12-07
> **dBuster said:**
> Slightly different problem for me.

Ubuntu 10.04.02 64 bit
64 bit flash both current and the beta from flashaid

With the beta I can't even view videos on youtube

other websites throw me an error 2046 or error 2032...

Can't seem to get around that.  Been told to upgrade but I am waiting for 12.04 before thinking of that.  Errors occur in any web browser I try.

Hi dBuster.
While I am trying to find a solution for myself, here's something I can contribute to you.

[I]Edit: wrote about flash-aid... realised he is already using it.
[/I]

---

### Post by katya_sehgal on 2011-12-11
No updates yet?
I had disabled all extensions and tried for a solution. It did not work.Is there any other clash that I could check for?

---

### Post by dBuster on 2011-12-13
Personally I had received a kernel update and now for the most part my flash is working.  However I can't use some features such as mass uploads of photos for either of the two major sites I upload to, one being snapfish and the other facebook.  I still need to do the old fashioned pick one at a time and then upload, or in some cases it lets me choose one at a time up to 12 then upload but when you have say 100 photos of the kids birthday party you want to upload it can be a pain in the you know what...

---

