---
title: "No gui on wubi install"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by millou68 on 2008-10-19
Hi,
  I am working with ubuntu(any linux for that matter) for the first time so I am trying to take it for a test drive on my windows laptop using wubi.  I using version 8.04 here.  So I follow instructions for the install and eventually it leads me to a blank screen.  When I hit the 'esc' key I get some kind of drum effect, but that is all.  No other keys give me any response.  What I can do is to ctrl-alt-f1 to a command prompt which seems to be working fine.  I get a prompt which allows me to log in with my orginal password.  However, without a gui the whole project is really of no use to me.  I am running this whole thing on a fairly basic winbook laptop.  Does anyone have any idea if this is a hardware problem or did I install incorrectly?  Thanks for your help in advance.

---

### Post by Paqman on 2008-10-19
When you're at the command line, try typing in:
```

startx

```
and let us know what it says.

---

### Post by Ptero-4 on 2008-10-19
Can you post the output of typing
```
cat lspci > lspci.txt
```
in the console.
To do this you'll need to do the ctrl-alt-f1 to get to the command prompt.
Type the above command (it sends the output of lspci to a text file so you can post it from windows), then either download tofrodos via aptitude (if you have the internet access configured) or from windows download metapad. Whichever route you choose, you need to convert the file from unix to dos format (with either the cli tool todos, or with metapad in windows), then just copy it between "CODE" tags in the forum.

---

### Post by millou68 on 2008-10-19
Here is the error message:
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.xo-lock and start again

Invalid mit-magic-1 keygiving up.
Xinit: resource temporarily unavailable (errno 11): unable to connect to x server
Xinit: no such process(errno 3): server error.

Thanks for the quick reply

---

### Post by millou68 on 2008-10-20
So I got it working.  I had to uninstall wubi, download it again, and reinstall under safe graphics mode.  What a headache.  Is Ubuntu for you? Good question.  Anyone thinking of taking the plunge should read this: [http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

I was looking for a windows substitute with better security.  After running ubuntu for 30 minutes I can see it is clearly not that.  Installs failed on missing pieces to get some standard websites up and running.  Command line suggestions from the system on what to do didn't work either.  Maybe time to pay up for mac os.

Thanks.

---

