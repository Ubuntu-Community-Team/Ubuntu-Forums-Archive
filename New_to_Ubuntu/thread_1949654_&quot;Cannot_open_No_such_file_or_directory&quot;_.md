---
title: "&quot;Cannot open: No such file or directory&quot; error"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by Manatee Magic on 2012-03-30
I'm trying to untar a .tar.gz file but it keeps coming up with the "Cannot open: No such file or directory" error. here:

$ tar xvfz tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz
tar (child): tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

the file name is tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz 

Am I missing something? What's wrong?

EDIT: Another:

$ cd tor-browser_en-US
bash: cd: tor-browser_en-US: No such file or directory

Apparently my OS cannot find any file. I would appreciate it if I could resolve this error. Thanks!

---

### Post by jerome1232 on 2012-03-30
Is their a particular reason you don't just double click the file and extract it like that?

---

### Post by chipbuster on 2012-03-30
EDIT: Apparently, a long time ago, I was an idiot or confused, or both.

This might sound like downright stupidity from me but....have you tried swapping around the order of the arguments? I seem to remember having some issues with that a long time ago, and I'm not sure if it was just my rig. Try xvzf or xzvf.

Also, you might try the j option for kicks and giggles. Sometimes, the files are mislabeled, although that doesn't look like the issue judging from your logs.

---

### Post by TeoBigusGeekus on 2012-03-30
> **chipbuster said:**
> This might sound downright stupidity from me but....have you tried swapping around the order of the arguments? I seem to remember having some issues with that a long time ago, and I'm not sure if it was just my rig. Try xvzf or xzvf.

Also, you might try the j option for kicks and giggles. Sometimes, the files are mislabeled, although that doesn't look like the issue judging from your logs.

What he said.
The f switch has to be last, near the filename; also, you don't need the z switch, tar can recognize the file format automatically, ie.
```
tar xvf tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz
```

---

### Post by jerome1232 on 2012-03-30
now whatever gave you guys that silly idea. The op simply isn't giving the correct path. There are easier ways to do this unless the op is on a command line only install, which I highly doubt. It's as simple as a double click.
```

voiceserv@voiceserv:~$ tar xfv test.tar
public_html/
public_html/index.html
public_html/images/
public_html/images/html-logo.png
public_html/images/bridge.jpg
public_html/images/background.jpg
public_html/images/ubuntulogo.png
public_html/Video/
public_html/Video/new_screencast2.webm
public_html/Video/Shinedown_-_What_a_shame.ogv
public_html/Video/new_screencast.webm
public_html/Video/Shinedown_-_What_a_shame.mp4
public_html/default.css
public_html/Audio/
public_html/Audio/12 The Unforgiven.mp3
voiceserv@voiceserv:~$
```

```
voiceserv@voiceserv:~$ tar fvx test.tar
public_html/
public_html/index.html
public_html/images/
public_html/images/html-logo.png
public_html/images/bridge.jpg
public_html/images/background.jpg
public_html/images/ubuntulogo.png
public_html/Video/
public_html/Video/new_screencast2.webm
public_html/Video/Shinedown_-_What_a_shame.ogv
public_html/Video/new_screencast.webm
public_html/Video/Shinedown_-_What_a_shame.mp4
public_html/default.css
public_html/Audio/
public_html/Audio/12 The Unforgiven.mp3

```

---

### Post by Manatee Magic on 2012-03-30
I'm trying to run commands on specific files but command line always gives the "no such file or directory" error. Here:


$ cd tor-browser_en-US
bash: cd: tor-browser_en-US: No such file or directory


This happens every single time. I've never had this problem before. Any suggestions?

---

### Post by chipbuster on 2012-03-30
Yep, just tested permutations of the command and they all seem to check out. Guess I was just crazy back then or something.

---

### Post by TeoBigusGeekus on 2012-03-30
> **jerome1232 said:**
> now whatever gave you guys that silly idea.

I've read it somewhere and that's how I use tar.
[http://superuser.com/questions/150777/tar-cannot-open-no-such-file-or-directory]("http://superuser.com/questions/150777/tar-cannot-open-no-such-file-or-directory")
[http://superuser.com/questions/211941/why-cant-z-be-the-last-command-line-option-to-be-used-with-tar]("http://superuser.com/questions/211941/why-cant-z-be-the-last-command-line-option-to-be-used-with-tar")

---

### Post by jerome1232 on 2012-03-30
> **chipbuster said:**
> Yep, just tested permutations of the command and they all seem to check out. Guess I was just crazy back then or something.

Or possibly it was true back then, and tar has since been patched :p, I don't know.

---

### Post by TeoBigusGeekus on 2012-03-30
> **jerome1232 said:**
> Or possibly it was true back then, and tar has since been patched :p, I don't know.

Could be...
But I always put f as the last switch just to be sure.

---

### Post by TeoBigusGeekus on 2012-03-30
Try giving the full path of the directory.
```
cd /path/tor-browser_en-US
```

---

### Post by jerome1232 on 2012-03-30
if you put a dash in front of your options it holds true (order matters). If you omit the dash as shown in the op and further posts, order doesn't matter.

edit: just realized it with more testing.

---

### Post by Manatee Magic on 2012-03-30
I tried more Terminal executions using specific file names and they didn't work either. So I can't do any execution on a specific file. I keep getting that same error.

---

### Post by TeoBigusGeekus on 2012-03-30
> **jerome1232 said:**
> if you put a dash in front of your options it holds true (order matters). If you omit the dash as shown in the op and further posts, order doesn't matter.

edit: just realized it with more testing.

Yeap, that's it.
I've also found [this]("http://unix.stackexchange.com/questions/13573/why-use-superflous-dash-to-pass-option-flags-to-tar").

---

### Post by Manatee Magic on 2012-03-30
Didn't work. 

$ cd /path/tor-browser_en-US
bash: cd: /path/tor-browser_en-US: No such file or directory

---

### Post by lisati on 2012-03-30
Threads merged because they seem to relate to the same (or similar) problem.

The command line in Ubuntu has a feature called "autocomplete" - what this means is that you can type the first few letters of a file or directory name on the command line, and then have the full file name pop up by pressing the "Tab" key.

---

### Post by Manatee Magic on 2012-03-30
> **TeoBigusGeekus said:**
> Yeap, that's it.
I've also found [this]("http://unix.stackexchange.com/questions/13573/why-use-superflous-dash-to-pass-option-flags-to-tar").

Example? I'm confused...

---

### Post by TeoBigusGeekus on 2012-03-30
> **Manatee Magic said:**
> Didn't work. 

$ cd /path/tor-browser_en-US
bash: cd: /path/tor-browser_en-US: No such file or directory

You shouldn't have put "path" in it; it should have been the actual path of the folder. 
Where is the tor-browser folder?

---

### Post by jerome1232 on 2012-03-30
> **Manatee Magic said:**
> I tried more Terminal executions using specific file names and they didn't work either. So I can't do any execution on a specific file. I keep getting that same error.

What do these commands show

```

pwd
ls
find / -name 'tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz' 2>/dev/null
```

---

### Post by Manatee Magic on 2012-03-30
> **TeoBigusGeekus said:**
> You shouldn't have put "path" in it; it should have been the actual path of the folder. 
Where is the tor-browser folder?

Desktop

---

### Post by TeoBigusGeekus on 2012-03-30
> **Manatee Magic said:**
> Example? I'm confused...

If you tar with dash, the order of the switches does matter:
```
tar -xfv blahblah.tar.gz
```
will give you an error message. The correct command would be
```
tar -xvf blahblah.tar.gz
```

But if you don't use dash, the order doesn't matter:
Both
```
tar xfv blahblah.tar.gz
```
and
```
tar xvf blahblah.tar.gz
```
will give you correct results.

---

### Post by TeoBigusGeekus on 2012-03-30
> **Manatee Magic said:**
> Desktop

So, the correct path is
```
cd ~/Desktop/tor-browser_en-US
```
~/ stands for /home/yourusername/

---

### Post by Manatee Magic on 2012-03-30
> **jerome1232 said:**
> What do these commands show

```

pwd
ls
find / -name 'tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz' 2>/dev/null
```

$ pwd
/home/will


$ ls
android-sdk-linux                   Documents                     Pictures
avast4workstation_1.0.6-2_i386.deb  Downloads                     Public
brasero.bin                         examples.desktop              Templates
brasero.cue                         minecraft_alpha_1.1.2.tar.gz  Ubuntu One
Data                                Music                         Videos
Desktop                             New Playlist.m3u

$ find / -name 'tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz' 2>/dev/null
/home/will/.local/share/Trash/files/tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz

---

### Post by jerome1232 on 2012-03-30
It's in your trash... restore it from there, to your desktop, then from a terminal type
```
cd Desktop
tar xvf tor-browser-gnu-linux-i686-2.2.35-9-dev-en-US.tar.gz
```

---

### Post by Manatee Magic on 2012-03-30
> **TeoBigusGeekus said:**
> So, the correct path is
```
cd ~/Desktop/tor-browser_en-US
```
~/ stands for /home/yourusername/

It worked thank you!

---

### Post by TeoBigusGeekus on 2012-03-30
> **Manatee Magic said:**
> It worked thank you!

Good. Now you can untar your archive (if it resides in that folder that is).

---

