---
title: "[SOLVED] Python UberNoob!"
date: 2007-10-26
forum: Programming Talk
---

### Post by CaptainInsaneO on 2007-10-26
Ok, I'm going to feel really stupid when I get the answer to my question because I know it's probably pretty simple. However, I've just started learning python about 3 days ago, so please bear with me in my frustration.

My problem is that I'm trying to get a program to run (see code below). It actually RUNS fine, I've made it executable with chmod and when I double click my file Ubuntu says that's it's an executable text file - do I want to run it or display it? If I click Run nothing happens. If I click Run In Terminal, the program runs in terminal but as soon as any input is given, terminal exits. I can run this program in IDLE perfectly fine and everything is magic.

Oh, and I've got the file in my user's /home directory, and when I try to run it from terminal by issuing ```
~/lol.py
``` it ALSO runs ok.

My ultimate question here is, is there any way to just run the program in terminal without having to choose how to run it or having it exit at the end before you see the output? This is so frustrating because I've searched for the solution but every Python program I've seen ends just like mine: it just ends.

```
#!/usr/bin/python
name = raw_input("What's your name? ")
if name == 'Nelson':
        print 'Whoa! You wrote this! Can I have your autograph?'
else:
        print 'Hello there', name
```

Also, I apologize for the whirlwind of info in one post, but when I'm answering questions in Absolute Beginner's Talk I enjoy more information, not less. I'm trying to do everyone a favor, sorry if I just took up half your day. :(

---

### Post by LaRoza on 2007-10-26
at the end, put ```
raw_input("Press any key to continue...")
```

This will keep the shell open. There are other methods too.

[php]
#!/usr/bin/python
name = raw_input("What's your name? ")
if name == 'Nelson':
        print 'Whoa! You wrote this! Can I have your autograph?'
elif name == "LaRoza":
        print "Whoa! You fixed this? Can I give you money?"
else:
        print 'Hello there', name

raw_input("Press any key to continue...")
[/php]

---

### Post by CaptainInsaneO on 2007-10-26
Yep. I knew it was freakin' simple. Thanks so much! I still have a lot of learning to do. Tried C++ years ago but gave up after a couple months. (Never try programming C++ on an iMac. Bleh)

Thanks for the tip, and the "addition". I must say, it really gives this program some *pop*. lol

Can you point me in the right direction to learn about those "other methods" you speak of? Thanks a million for your great help!

---

### Post by LaRoza on 2007-10-26
> **CaptainInsaneO said:**
> 
Thanks for the tip, and the "addition". I must say, it really gives this program some *pop*. lol

Can you point me in the right direction to learn about those "other methods" you speak of? Thanks a million for your great help!

No problem, when I first started (with C++), I was just as confused.

The other methods include:

* using a loop that exits if a condition is reached.
   [php]
   while age != "":
        age = raw_input("How old are you? ")
        if age < 18:
            print "You are too young"
        else:
            print "Hi" 
   [/php]

* Using "sys.exit()" explicitly. Good idea in some cases.
* Just using "raw_input()" with no prompt, I was just copying Windows "PAUSE" command. Where is the "any" key?
* Using "os.system('PAUSE')" or "os.system('sleep')". Not really a good idea, but it works.

-EDIT Sleek desktop!

---

### Post by CaptainInsaneO on 2007-10-26
How many times am I going to say thanks in one thread?! :lolflag: Thanks!

I realize that with a little logical thinking I could probably (someday. maybe.) come up with these ideas on my own. I did try Google (GIYM-Google It You Moron) and only posted a thread as a last resort. Seeing as to how simple the solutions to my problem are, I need to hit Google a little harder next time.

I think I'm done for the day, but I'll try some of those suggestions later on.

Thanks for the desktop comment. :) Usually I have a gDesklets sidebar running but for some reason it won't start right now and I haven't felt like restarting my xserver (I'm having a pretty lazy day here, cut me a break. lol). You can see more pics (if you're interested) in [this thread]("http://ubuntuforums.org/showthread.php?t=569470").

---

### Post by LaRoza on 2007-10-26
> **CaptainInsaneO said:**
> 
I realize that with a little logical thinking I could probably (someday. maybe.) come up with these ideas on my own.

Thanks for the desktop comment. :) Usually I have a gDesklets sidebar running but for some reason it won't start right now and I haven't felt like restarting my xserver (I'm having a pretty lazy day here, cut me a break. lol). You can see more pics (if you're interested) in [this thread]("http://ubuntuforums.org/showthread.php?t=569470").

Don't tell anybody, but I asked the same question to a programmer when I started. 

My computers are a poor representation of Linux, as I use a simple, 2d theme in Fluxbox that I wrote. It is only black, no icons or panels, and the menu's and windows have a think white outline, with white text. It is as simple a GUI as I could manage.

---

### Post by pmasiar on 2007-10-27
To avoid many confusions, try to follow some good tutorial. I collected which are IMHO the best, see my sig.

---

