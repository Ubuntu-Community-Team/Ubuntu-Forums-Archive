---
title: "[SOLVED] can't get Frostwire to launch"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-03
I installed Java 6 jre and its dependancys.  I downloaded and installed Frostwire.  The installer states all dependancys are met.  I can see it in Applications.  I click on it and zippo, nothing happens.  I deleated it and reinstalled it thinking I had some software issues.  But it just won't launch.

I am using 8.04.  I did have Limewire installed on my previous 7.10 installation.  I just can't figure out where I goofed.  I am obviously missing something.  Any suggestions?  BTW I wanted to give Frostwire a try.  It is supposed to be better than Limewire.  I did try Gnutella, I just could not figure out how to make it work.  Too much stuff in there for me.  Just wanted a simple PTP client.

Mark Shuman

---

### Post by perlluver on 2008-05-03
> **phread59 said:**
> I installed Java 6 jre and its dependancys.  I downloaded and installed Frostwire.  The installer states all dependancys are met.  I can see it in Applications.  I click on it and zippo, nothing happens.  I deleated it and reinstalled it thinking I had some software issues.  But it just won't launch.

I am using 8.04.  I did have Limewire installed on my previous 7.10 installation.  I just can't figure out where I goofed.  I am obviously missing something.  Any suggestions?  BTW I wanted to give Frostwire a try.  It is supposed to be better than Limewire.  I did try Gnutella, I just could not figure out how to make it work.  Too much stuff in there for me.  Just wanted a simple PTP client.

Mark Shuman

Run in a terminal, sudo update-alternatives --config java and make sure Sun Java is selected and not Open JDK.

---

### Post by phread59 on 2008-05-03
It throws back command not found.  Typed it exactly as you had it, hmmm.  I'm wandering if there is a plug in or program I just don't have loaded?  I know it was simple in 7.10.  Just can't remember what I did.  BTW what part of PA you from perluver?

Mark Shuman

---

### Post by perlluver on 2008-05-03
> **phread59 said:**
> It throws back command not found.  Typed it exactly as you had it, hmmm.  I'm wandering if there is a plug in or program I just don't have loaded?  I know it was simple in 7.10.  Just can't remember what I did.  BTW what part of PA you from perluver?

Mark Shuman

New Castle, above Pittsburgh.  And this command should work, I got it to work.  sudo update-alternatives --config java

edit:  Do you have Sun Java installed along with Sun JRE plugin?

---

### Post by phread59 on 2008-05-03
Hi again, no soap, keep getting "sudo update-alternatives--config: command not found".

BTW I went to school in Monaca at the PSU campus there for 2 years.  Been through New Castle only a few times over 20 years ago.  Enjoyed my time out there though.  I'm back home in Central PA for over 25 years.

Only a thought but maybe I need to log out and log back in for it to take effect.  Didn't have to do that with Limewire.  BTW tried uninstalling Frost and installing Lime.  no joy either way.  So there must be a software dependancy issue somewhere.  I shut down Firestarter to see if that was the culprit, didn't help.  Seems weird that I cannot get it up and going in 8.04 when I had it going in 7.10.

One last thought.  Frostwire somewhere in the docs I skipped through stated this was for 586?  Is this a kernel thing?  I'm running mostly 386 stuff.  I'm using 32 bit 8.04.  Does this help?

Mark Shuman

---

### Post by perlluver on 2008-05-03
```
sudo update-alternatives --config java
```

Copy and paste that into the terminal.

---

### Post by phread59 on 2008-05-03
BINGO!!!!!!!!!!!  We have ignition Mr Scott.  I have absolutely no idea why when I typed it in the terminal it flunked.  I cut and pasted yours in and there it was.  I was set to the open source version.  Reset to Sun Java 6 bin and reclicked Frostwire.  The install wizzard came up and I'm all set.  Thank you very much.  Just wonder what is wrong with my terminal?  Had a few other commands dork on me even though I typed them in correctly.  I may just ask about this.  Thanks again Perllover, thank you very much.

Mark Shuman

---

### Post by perlluver on 2008-05-03
> **phread59 said:**
> BINGO!!!!!!!!!!!  We have ignition Mr Scott.  I have absolutely no idea why when I typed it in the terminal it flunked.  I cut and pasted yours in and there it was.  I was set to the open source version.  Reset to Sun Java 6 bin and reclicked Frostwire.  The install wizzard came up and I'm all set.  Thank you very much.  Just wonder what is wrong with my terminal?  Had a few other commands dork on me even though I typed them in correctly.  I may just ask about this.  Thanks again Perllover, thank you very much.

Mark Shuman

You are welcome, when you retyped it, it didn't have spaces in it, the spaces are important, also upper and lowercase letters, are case sensitive.

---

### Post by locosmurf on 2008-05-03
> Hi again, no soap, keep getting "sudo update-alternatives--config: command not found".

phread59,

The reason you couldn't get the command to work is that you didn't put the space in between "alternatives" and "--config". Just make sure you type commands carefully in case something doesn't work the first time. :)

---

### Post by phread59 on 2008-05-03
I have been trying to configure Java all day today.  I type in "sudo update-alternatives--config java"  and terminal sends back "sudo update alternatives--config: command not found"

 Perllover put it in a box and told me to cut and paste it in.  I did so and voila there it was.  I have had other issues where I would type in commands and get a command not found error comming back.  Is there a problem with terminal.  BTW I'm using Gnome's terminal.  Never tried kterminal.  Maybe I should just to see.  I do have the KDE desktop installed because I like playing with it.  I use Gnome when I want to get serious.  Any suggestions.

Mark Shuman

---

### Post by dcook32p on 2008-05-03
From the earlier thread, it looked like you weren't putting a space between "update-alternatives" and "--config".

---

### Post by tacutu on 2008-05-03
that's probably due to typos. it is
sudo update-alternatives --config java
not
sudo update-alternatives--config java
(i.e. there is a space before --config)

---

### Post by phread59 on 2008-05-03
OK I see that.  Dummy just couldn't wrap his brain around a syntax error.  Been a long time since I actually did any programming.  Stinkin Windughs got me out of using anything like terminal for so long I forgot a lot about syntax.  I will try to be more careful in the future.  Thank you for pointing out such a foolish omission on my part.

Mark Shuman

---

### Post by phread59 on 2008-05-03
You fellows are absolutely correct.  I am going to apologize.  I just could not see the space and had the syntax wrong.  Thinking back to other issues I think it was my syntax that may have been the cause.  As I stated in my other thread it has been forever since I had to program.  My syntax just sucks.  I wish there was a good document on Ubuntu syntax.  Commands and what they do and proper syntax would be a very good thing.  If anyone knows where one is I would love to go and print it.

BTW where are the thread tools?  There used to be an option to ignore a thread or mark it solved.  With the new format I have not been able to find it.

Mark Shuman

---

