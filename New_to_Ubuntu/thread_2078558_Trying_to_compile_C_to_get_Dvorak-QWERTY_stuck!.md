---
title: "Trying to compile C to get Dvorak-QWERTY: stuck!"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by DerekP on 2012-10-31
Hi all,

I don't know C, and i've never compiled anything in my life. In Windows i use AutoHotKey to achieve the same. I tell you, until i found this i thought my run in Linux would be VERY short-lived. I wish Ubuntu would provide this as a keyboard layout - like OS-X does :(

What i 'need' is Dvorak, with QWERTY super/alt/ctrl keys, and this program is said to deliver it:
[http://code.google.com/p/dvorak-qwerty](http://code.google.com/p/dvorak-qwerty)

However, i just can't get it to work. I followed these instructions:
[http://askubuntu.com/questions/143573/is-there-any-way-to-use-qwertys-keyboard-shortcut-position-while-the-dvorak-lay](http://askubuntu.com/questions/143573/is-there-any-way-to-use-qwertys-keyboard-shortcut-position-while-the-dvorak-lay)

I want the full keyset, so tried:
gcc xdq.c -o xdq -std=c99 -O2 -lX11 -DXQD_GREEDY

(is that a "0" or a "O"? i tried 0 first, but it didn't compile, so i assume it's an O).

When i tried to run it via terminal "./xdq", i got this:

> Failed to grab 280 key combinations.
This is probably because some hotkeys are already grabbed by the system.
Unfortunately, these system-wide hotkeys cannot be automatically remapped by
this tool.  However, you can usually configure them manually.

...and then the terminal hangs and if i try to close it, it says it'll kill the process to close it. Which i do :)

Help?!

---

### Post by DerekP on 2012-11-04
Please help, if i don't get Dvorak with QWERTY super keys - i will not be using Linux. It's simply not an option without it (i tried).

Thanks.

---

### Post by squakie on 2012-11-04
If you are running 12.x, go to system settings, then click on keyboard.  Click the "+" sign to add - you get a wide selection including several for English Dvorak.  I personally don't use it, so I couldn't tell you how they work.  There appears to be some there where it sounds like you might be able to remap certain keys while leaving the keyboard as dvorak.

Wish I could tell you more - I just don't use the Dvorak keyboard layout.  Tried it on the side many, many, many years ago and I just couldn't adjust to it.

---

### Post by DerekP on 2012-11-05
Believe me, i've looked around, this is the only thing i've found.

Last time i tried, i was in Ubuntu 12.10. I've rebuilt to Ubuntu 12.04.

This time it compiled without any errors, but when i run it, it doesn't seem to alter the behaviour at all. How do i tell if it's actually running?

EDIT: Figured that bit out.

I've actually got a working file now - except it does not capture the greedy (super) keys, despite my attempts.  I'm presuming there is something wrong with the syntax.

---

### Post by DerekP on 2012-11-11
This is driving me insane. What the hell do i have to do?

Experimenting (removing the 'if greedy' bit from the source), i accidentally over-wrote my working copy of the compiled file. Needless to say, any and all compilation  attempts with either the old source or the modified source yield absolutely no result.

Why?

---

### Post by squakie on 2012-11-11
Delete what you've done.  If you need the xdb.c program again, download the source.  Look in the c source and just copy/paste the compile line to a terminal window and press enter.  It mentions a lib that is needed but at least for me in 12.10 I already had the lib.

The program compiled like that fine for me.

Next, I went to system settings, keyboard.  I clicked on layout and then the "+" key and selected English (Dvorak) and added it.  I then highlighted the only other entry I had - English (US) and pressed the "-" sign to delete it, so the only option I had was English (Dvorak).  I then closed out of settings.

Next I opened a terminal window (not with the function keys, but actually opening "Terminal" - the instructions say you have to do it that way).  I changed to the folder where I had the compiled xdb.c program and typed ./xdb and pressed enter.  This starts the program, and it stays active until you close it.  It has to be the gnome terminal - not one opened by the function keys.

Next I opened gedit and opened the xdb.c program source using the mouse, then pressed ctrl X and it exited.  Typing on the other keys showed they were indeed mapped to Dvorak, so it appears to me it works fine.  I closed the terminal so that it would in turn kill xdb so my control keys would be back to normal. 

There are notes in the on the askubuntu page you pointed to about only needing the greedy option (and the correct format for that gcc option) if you are also wanting to map things like alt keys.  I didn't try that so I can't comment on what may be needed to make that part of things work.

So, as long as kdb is running in a terminal window, I can open other programs and the control key functions work as indicated in the wiki.  If you run kdb by other than in a actual terminal window it won't work - you can't use the keyboard shortcut to run the command.  If you close the terminal window you will lose the functionality until you run it again in a terminal window.

Whether there is some way to start this in startup as some sort of detached terminal window I don't know - I'd have to look and try somethings to try to figure that out.

---

### Post by DerekP on 2012-11-12
Thanks for trying Squakie.

My keyboard is already Dvorak - it's what i type in - it's all i type in. So i didn't need to change it to 'normal' English. I followed your advice and added English US so i can choose. I tried to compile it while in QWERTY (Eng US) to see if that made a difference (of course it shouldn't) and it didn't.

I've compiled the original file and run it from the the terminal, and i've tried to run it via double-clicking the binary and it just doesn't work. It's running, but it doesn't change my key mappings.

But this is interesting, right now my screen tells me i'm in "en2" - which is supposed to be English (US) - QWERTY - but i am typing - right now - in Dvorak... i'll be back in a minute....

EDIT: Nope, nothing works. Note it compiles fine, the program just simply does not work. Now, it DID work for me twice (once only on a different PC, once only on this one), until i accidentally copied over it with a bung copy.

I would LOVE to know what i'm doing wrong. It's just a bunch of code - compiled using the instructions provided. Note one of my earlier posts, i DID get it to work once, using EXACTLY the instructions i myself posted in this thread. Since then, nothing. OMG it's like Windows 3.1 frustrating!

My experiment with Linux will go nowhere until this is sorted :(

---

### Post by squakie on 2012-11-12
I would try  "make uninstall" in a terminal first, then:

- delete the existing source code and executable
 
- download everything all over again so you know you are working with the correct source code

- remove the English(US) from the keyboard mapping if it still shows in settings EDIT: so only English(dvorak) shows 

- copy and paste the compile line directly from the comments in the C source code - that's all I did.

- I'm sure you are, but go through the menus (if Unity, fill the search string with ter) and select the terminal there - that's also what I did.

- be sure to start the program before you open anything you want to use the remapping in.

- try it with a simple gedit of some dummy text and do the ctrl-W

Not knowing much else, that's all I did.  Like I said the ctrl-W worked for me.  If you are trying to go beyond just those keys, I haven't tried that simply because I normally don't use shortcut keys.

If you could tell me what application you are using and what you are pressing for keystrokes that don't work, I could try it again with that.

EDIT:  just reread your initial post - the terminal isn't hanging - it's running the program.  You have to leave that terminal window just as is and run your applications.  If you close that window or in some other way return to the command line, the program is no longer running so the key mapping will not change to what you want.  If you haven't, try it that way and then we can try to figure out how to get it running by other means, if possible.

---

### Post by critin on 2012-11-12
> What i 'need' is Dvorak,

During installation of ubuntu, there is a section to configure the keyboard.  Did you use it to choose Dvorak?

---

### Post by squakie on 2012-11-12
Just go system settings/keyboard - you can see your currently selected keyboard mapping - click on the "+" then scroll down to find the dvorak you want (like English(devorak)).  But the op has supposedly already gotten that - they need to make the ctrl functions work as they stated.  The program does that.

---

### Post by DerekP on 2012-11-13
> **critin said:**
> During installation of ubuntu, there is a section to configure the keyboard.  Did you use it to choose Dvorak?

Hi Critin,

I did. This thread is about getting QWERTY ctrl/alt/super keys with Dvorak layout.

---

### Post by DerekP on 2012-11-13
> **squakie said:**
> But the op has supposedly already gotten that - they need to make the ctrl functions work as they stated.  The program does that.

Yeah, bugger of a thing. It's really bizarre, other people have said that it 'just doesn't work' for them either. I wonder if Ubuntu/Unity is the problem. I might try to install Cinnamon, compile it in there, see if that works.

---

### Post by squakie on 2012-11-13
If you need the alt keys, etc., beyond just the ctrl keys, I didn't try that yet - I'd have to recompile with that option and then try to test it.

Do you have an app and certain keystroke(s) that don't work for you so that I might try those as well to see if they work or not for me?  I don't know if doing so will be of any help or not - I was just hoping it would work for me and then we could try to seek out the differences.  But, as I said before, I'm not a Dvorak user, so I don't really know what/how to test without you pointing to some app and specific problem if at all possible.

Wish I could be of more help and just say of course - it's this, but all I can do is just keep trying it here to see what might happen.

---

### Post by DerekP on 2012-11-13
Hi Squakie.

I appreciate what you've tried so far. It's head scratching and no mistake. I mean, i should just be able to compile it, run it and enjoy it.

I compiled it in Cinnamon, just thinking that maybe Unity was bugging it somehow (shrug) and when i run it i only get "Failed to grab 3 key combinations." instead of 32 or whatever it was in Unity.

But it still doesn't actually work.

I run it, then load gedit and try copy/paste using QWERTY shortcuts and it doesn't work. The usual Dvorak ones work. I don't need this setup for any particular programs... just all programs :) If you look at the Dvorak keyboard, it really wasn't designed for Microsoft's use of shortcuts that have now become the defacto standard (WordPerfect was first, but they had different shortcuts, so MS made their own and now they rule the world).

I've got a friend who knows C#, but i don't think he has a linux build. I'm sure he could tell me if there is any problem with what /i'm/ doing, though perhaps not why it doesn't work if what i'm doing is what i should be doing.

---

### Post by squakie on 2012-11-13
I'll try running it again and see if ctrl-C and ctrl-V work.  Since I used ctrl-W, I assumed it would.  I'll post back after I've done that.

Now this IS weird!  I just tried the EXACT thing I did before and it didn't work now!  I also tried the ctrl-c and ctrl-v and they weren't working - I still had to use the dvorak c and v keys.

I'm quite confused at this point.  I'll try to take a look at the code a little later tonight.

---

### Post by DerekP on 2012-11-14
I'm relieved it's not just me, but i didn't wish it on you :)

My colleague hasn't been at work to look at, i'll tackle him as soon as i can.

---

### Post by squakie on 2012-11-14
I put a couple of statements in the code last night and recompiled it.  Those statements should have told me where in the code it was and yet I got nothing.  I'll be digging into it more later tonight.

It is indeed very strange!  It may have something to do with how it's trying to capture keystrokes.

---

### Post by squakie on 2012-11-15
I put some more tracing in the program, and it doesn't even look like it gets the keystrokes.  I may need to do a lot more digging into this, the functions it is using, and whether they are fully compatible with Ubuntu.  I might be something like which version of X, etc., as to whether or not it works.  I'm no expert on any of that, but I can try to look it up and see how the code is trying to implement these things versus what can actually be done.

Just a quick glance, it appears it may only be setting the window to the window that xdq is run in, which obviously would mean it's not doing anything with keystrokes in a new window like gedit.  I'll try to research this further to see if I can understand it better.  It is using Window as a default from the root display, and it only sets the Window once.  *IF* (and that's a big if) I understand correctly, the xgrabkey is working on the default window - and that would be the terminal the program is run in.  However, this X window programming to grab input, etc., is a completely foreign thing to me - I'll be learning as I go.  Hope I can find something.

---

### Post by squakie on 2012-11-16
I added some more fprintf's to the program to see where it's not working:
```
fprintf(stderr,"\nbefore event loop\n");

  for (;;) {

    XEvent event;
    XNextEvent(display, &event); 


fprintf(stderr,"\nchecking event\n");

    switch (event.type) {
      case KeyPress:
      case KeyRelease: {
        if (event.xkey.send_event) {
          fprintf(stderr, "SendEvent loop?\n");

fprintf(stderr,"\nat sendevent loop err?\n");

          break;
        }
        // Remap the keycode.
        // NOTE(kenton):  I think this conditional is always true but better
        //   safe than sorry.

fprintf(stderr,"\nready to remap\n");

        if (event.xkey.keycode >= 0 &&
            event.xkey.keycode < arraysize(keycode_mapping)) {
          int new_keycode = keycode_mapping[event.xkey.keycode];
          if (new_keycode != 0) {

fprintf(stderr,"\nremapping key, new keycode: %i\n",new_keycode);

            event.xkey.keycode = new_keycode;
          }
        }

        // Find the focused window and send the event to it.
        int junk;
        XGetInputFocus(display, &event.xkey.window, &junk);
        XSendEvent(display, event.xkey.window, True, 0, &event);

        break;
      }
      default:
        fprintf(stderr, "Unknown event: %d\n", event.type);
        break;
    }
  }
}

```If you find the:

fprintf(stderr,"\nbefore event loop\n");

  you'll notice that it is trying to trap the key and remap it.  However, it prints nothing beyond this point, whereas it should be either printing there's an error, or it should be printing that it is remapping the key.  None of this happens.  It leads me to think that perhaps it is not actually detecting keystrokes from the (as an example) gedit window.

Right now I don't understand enough to even guess as to why.  I've been trying to find out what some of the X calls are doing, but that's a slow learning process for me as I've never used those before and so far I am unable to locate a document that just shows examples and what they are doing, though I have found a big X document.

If I can get this figured out I will post again.  I just don't know how soon that might be.

---

### Post by Aaron Christianson on 2012-11-17
I realize this may not be helpful, but I'm curious as to what drove you to us a non-standard version of a non-standard layout. This actually relates directly to the Unix philosophy, a tenant of which is "choose portability over efficiency."

This is the thing that has kept me from switching to Dvorak. Well, that and Vim.

Good luck with your compiling, in any event.

---

### Post by squakie on 2012-11-17
After many changes and testing tonight, it appears the xnextevent isn't working, at least not in the window the editor is in.  This may again come down to the display still being set to the terminal window that xdq was launched in.  For now, I'm headed off to some sleep and will try looking more at this later.  I did see another person posting in another thread with a sample program trying to trap events, and they said the keypressed and keyreleased traps don't work.  However, we aren't even getting that far.  It never "returns" from the xnextevent, indicating the display/window it thinks it is dealing with has not detected any key presses.

---

### Post by squakie on 2012-11-17
I posted for help in the programming forum, as it appears to me it is only looking at keystrokes in the X window that xdq was actually started in - i.e., the terminal window.  However, since this X stuff is all new to me I wanted to post in the programming forum to (1) see if I'm understanding it correctly, and (2) hope someone might be able to correct me if I'm wrong but also help make the program work.

I'll post back when/if I hear something or if I dig further into the usage of the X calls and see something stand out.

---

### Post by DerekP on 2012-11-19
Wow, that's very gracious of you. Thank you very much, i appreciate it.

---

### Post by DerekP on 2012-11-19
> **Aaron Christianson said:**
> I realize this may not be helpful, but I'm curious as to what drove you to us a non-standard version of a non-standard layout. This actually relates directly to the Unix philosophy, a tenant of which is "choose portability over efficiency."

G'day Aaron. The QWERTY shortcuts came about because when i was learning Dvorak, the thing that annoyed was the cut/copy/paste. I found a solution in Windows via AutoHotKey and never had to worry about it again.

When i saw Windows 8, i decided to rebel and try Linux (i am happy with Windows 7), and because i build PCs for charitable purposes and i wanted to build PCs that did not have Windows licenses stickers with Ubuntu.

I decided to try Dvorak because i was getting sore using QWERTY and to demonstrate the folly of an economics theory that the best wins out. Obviously, people use Windows because people use Windows. Same applies to QWERTY. So in a twisted logic, Linux users should use non-standard everything - if it's better! :P

I have occasionally wondered if it has been worth it. But switching back now seems, well, backward.

---

### Post by donmccurdy on 2013-02-26
I seem to be having this same problem - xdq compiles and runs, but simply doesn't work. If anyone has found a workaround I'd be interested! 

As far as using a non-standard version of a non-standard keyboard, I use OSX at home, for which there's a Dvorak-Qwerty keyboard layout (it comes standard with the OS) that does what xdq is supposed to do. So I've only ever had to use qwerty shortcuts, which are much better optimized than pure dvorak.

---

### Post by squakie on 2013-03-02
I haven't forgotten the problem - I just haven't found a solution.  No answer from the programming forum.  I did some more research and it appears the calls that program is using are not working with X.  I even created my own little program to trap opening a window, keystrokes, closing a window, and none of those events ever seem to trapped.  I would suspect, but don't know, it either some incompatibility between the calls and X, or perhaps what version of X.  I still not found anymore information or fix yet.  I hope if someone else knows the answer that they will post as well.

---

### Post by donmccurdy on 2013-03-17
For whatever reason, xdq started working for me. Haven't installed anything particular (aside from the periodic software updates) but I tried running it every morning at work and one day (maybe two weeks ago?) it started working and hasn't broken since. I have no idea why, unfortunately. I was getting pretty close to ordering an Arduino and programming it as a keystroke replacer.

---

### Post by squakie on 2013-03-17
I think there may have been an update to X recently.  I'll go give it a try again and see what happens.

You may want to PM the OP and tell them they might want to try again.

---

### Post by squakie on 2013-03-18
Well, I just recompiled xdq.c and started it in a terminal window (./xdq).  Then opened gedit, typed in garbage, used the mouse to select part of it a copy it, then tried cntrl-V and cnrtl-v both to try to paste it - it didn't work.  So, at least for me, the problem still exists.

So, did you install the x11 client side development package to get libX.h or did you install it some other way?

---

### Post by donmccurdy on 2013-03-20
Yes, I was running it via terminal window and have since set the script to run on startup. I'm fairly sure I used apt to get libx.h, could be wrong though. Here's the output when I run dpkg --get-selections | grep libx11

libx11-6:amd64				install
libx11-6:i386				install
libx11-data					install
libx11-dev:amd64			install
libx11-doc					install
libx11-xcb1:amd64			install
libx11-xcb1:i386				install

---

### Post by DerekP on 2013-04-22
Hi guys, thanks for continuing to look into it. I'm sure for you it's more of that Linux mindset "what the hell is going on, how do i fix it?!" than "i sure want to help that guy" :)  I had actually given up hope, and even if you manage to 'fix' it, i worry that the problem will return at some point, perhaps with an update to something.

donmccurdy, i hear what you're saying about the Dvorak-QWERTY in OS-X - do you use Linux much or are you just trying it out? (just curious).

---

### Post by donmccurdy on 2013-04-22
> **DerekP said:**
> ... I had actually given up hope, and even if you manage to 'fix' it, i worry that the problem will return at some point, perhaps with an update to something.

donmccurdy, i hear what you're saying about the Dvorak-QWERTY in OS-X - do you use Linux much or are you just trying it out? (just curious).

Yeah that's my concern too. I've been using Linux consistently since January as it's the preferred development environment where I work, but had really only used it to manage my VPS before that (i use it for my website and little one-off projects). So I'm still more comfortable in OS X, really.

---

### Post by Dreamer Fithp Apprentice on 2013-04-22
Not what you asked for, but given your objective, you may be interested. Reason Magazine, put out by the Reason Foundation, ran an article about the history of the Dvorak keyboard more than a decade ago. At the time, I had been useing Dvorak for maybe 5 or 6 years, and I wondered why it seemed to me I was SLOWER than I was before I made the switch. Well that article explained it perfectly. I switched back and I was faster in less than a month. I can't give you the reference but they probably have it online and accesible to google.

---

### Post by DerekP on 2013-04-24
I haven't been playing with Linux/Ubuntu much lately. I've also stopped using Dvorak and gone back to QWERTY which, frankly, just feels wrong now. It's not the speed or familiarity, it only took a couple of weeks to regain my old speed. It's the illogical layout of QWERTY that irks me. Learning Dvorak was SO much easier than learning QWERTY and by large, the key placement was much better. It's ONLY cut/copy/paste that is a problem. In my job, there can be times where i spend hours using it and Dvorak was about 1/5 as efficient.

Now i'm wondering, what about Colemak? I realise i can Google this, but does anyone have experience with Colemak and with Linux in particular?

Cheers guys.

Dreamer, i'll have a quick look at the Dvorak article you mention (if i can find it). Before going to Dvorak, i did read a fair bit about it so i'm pretty familiar with it's history though. Dvorak's history has a parallel with Linux imo. Everyone uses QWERTY because everyone uses QWERTY, not because it's better. Everyone uses Windows because everyone uses Windows, not because it's better. Though, i love Windows 7, from a users perspective, i prefer it to any Linux distro i've tried (not many).

---

### Post by Dreamer Fithp Apprentice on 2013-04-28
Here it is:

[http://reason.com/archives/1996/06/01/typing-errors](http://reason.com/archives/1996/06/01/typing-errors)

On the left side of the page you have to click yes or no on 2 market survey type questions to read it (eg. "Do you have kids?" yes/no  -&- "Do you care about the amount of salt in your food?' yes/no to read the whole thing but that's it.

Wikipedia also has an article that touches on the same things.

I'm not a serious student of the affair but the bottom line seems to be:

There have been 2 main published sets of studies attempting to assess the effects of the Dvorak layout. The first group was done by Dvorak himself, was abominably designed and didn't really logically demonstrate anything beyond the fact that typists got better with training. Duh. The second was by a man named Strong and came to the opposite conclusions of Dvorak's. Nobody seems to question the soundness of the logic of Strong's study design but at least one writer seems to outright question his honesty and claims he had personal animosity for Dvorak.     Curiouser and curiouser. I've also seen allusions to studies that seemed to be in-house unpublished studies. There seems to be a lot of shrill tis/tis not sort of rhetoric out there on the issue. I suspect the origin of that lies in embarrassed error and wounded pride, perpetuated by pro and anti Dvorak zealots each unwilling to give up an over simplified "good story" and little motivation for anyone to really do good science in a transparent manner.

One thing seems clear : the oft repeated idea that qwerty was designed to slow typist down is false. Apparently the design intent was to arrange the keys so that the most common 2 letter combinations were located so that the one letter would be a left hand letter and the other a right hand letter causing the typist to alternate typing keys with left fingers and right fingers more often than pure chance would dictate. Ironically, this was a major goal of the design of the Dvorak layout as well, although for different reasons.

---

### Post by DerekP on 2013-05-05
The fastest typer in the world uses Dvorak for 212wpm :)

[http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard#History](http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard#History)
> Using the Dvorak Simplified Keyboard, she was able to maintain 150 words per minute (wpm) for 50 minutes, and 170 wpm for shorter periods. She has been clocked at a peak speed of 212 wpm. Blackburn, who failed her QWERTY typing class in high school, first encountered the Dvorak keyboard in 1938, quickly learned to achieve very high speeds, and occasionally toured giving speed-typing demonstrations during her secretarial career. Blackburn died in April 2008.

I'd been typing QWERTY for about 20 years and decided to learn Dvorak. After about three months my speed was pretty similar and i was fully touch-typing in Dvorak. I found it intuitive and logical, with better 'core' key placement. Often described is the home row can type about 300 English words in QWERTY vs about 3000 in Dvorak. Logically, this means less movement and faster potential speeds.

There are two disadvantages with Dvorak in my view (after about 2 years using it):
1. Cut/Copy/Paste (the others don't matter imo) -- software
2. It's slightly weighted to the right hand, which in the era of mouses is a slight disadvantage -- hardware

I'm no Dvorak zealot, but i think it's a shame that we're 'stuck' with QWERTY. I might try Coleman next, which addresses the cut/copy/paste and keeps more keys in the same place for easier conversion. As long as bloody Linux distros support it :)

---

### Post by Dreamer Fithp Apprentice on 2013-05-09
I don't think you need built in support so to speak. There are key remapping utilities that should let you reassign keys to support any layout you can imagine.

---

### Post by DerekP on 2013-05-27
Yeah, except Dvorak with QWERTY shortcut/super keys :D

---

