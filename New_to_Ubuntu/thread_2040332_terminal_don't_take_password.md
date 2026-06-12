---
title: "terminal don't take password"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by dolvita10 on 2012-08-10
hello want to work in terminal whatever I pasted he ask password but he is not reacting , so the cursur is not moving if I give in password?    need this have no audio with preview in openshot      working with ubuntu 12.04  ?   
hope this is the right place to post this?


please help

thanks ,david

---

### Post by MG&amp;TL on 2012-08-10
The terminal won't display any output when you type your password for security reasons. Just type it in and press return, if you've typed it correctly, you'll be authenticated, if not, you'll get a 'try again' message.

---

### Post by dolvita10 on 2012-08-10
yes but if i don' t copy and pasted , you are right and it works but try to copy and past the installation of openshot  , he also ask passwords but then terminal hangs   gnome terminal ?


I typed in the terminal before (copy paste) and than it words  but now the terminal hangs 

This was not so bad if I could install openshot with working audio in preview ,mean with the ubuntu software installer 

hope an answer?

---

### Post by anewguy on 2012-08-10
I don't really understand what you are saying - copy and paste 1 time, type in the next, where?

How about attaching some screen shots of what you are typing and where so we can get a better idea of what you are asking about.

Also, without knowing your hardware it's just a guess, but perhaps you should look and see if the sound is muted, or perhaps you need to install alsa mixer.

---

### Post by dolvita10 on 2012-08-22
[



I think the password case is solved  (one of the input I copyied and paste into terminal put my keyboard into extended mote ..>>> pasword not correct anymore )
Stil there is a problem with openshot still the preview is without audio . and the audio with vlc player is every time I start to play music or movie bad for a couple of seconds

even movieplayer has the same as vlc .      ------The backend of the sound system could be something wrong with . I don't know how to check that or better new installing that ???    what I mean I did not use alsa but something else . How do I find out whith system back end for audio am I using? and how to change it so in preview openshot I hear audio . and the other complains about movieplayer and vlc disappear.?        


QUOTE=anewguy;12163341]I don't really understand what you are saying - copy and paste 1 time, type in the next, where?

How about attaching some screen shots of what you are typing and where so we can get a better idea of what you are asking about.

Also, without knowing your hardware it's just a guess, but perhaps you should look and see if the sound is muted, or perhaps you need to install alsa mixer.[/QUOTE]

---

### Post by blackmail on 2012-08-22
to install openshot just type in:
```
sudo apt-get install openshot
```
then type in the password and press "y" if asked...

---

### Post by dolvita10 on 2012-08-22
> **blackmail said:**
> to install openshot just type in:
```
sudo apt-get install openshot
```then type in the password and press "y" if asked...
thanks It works to install openshot but still the same: preview without sound?

---

### Post by blackmail on 2012-08-24
If i may humbly suggest instead of openshot try kdenlive

sudo apt-get install kdenlive

it is an awesome program! just install and play with it, i like it much more and it looks more professional

---

### Post by dolvita10 on 2012-08-25
[thanks I installed it need to find out how to open a file like .wmv ? if i look in directory i keep my videos this program don"t regonize them ? so can not open what do i do wrong.? 
well I play with it a bit more ???!!!


QUOTE=blackmail;12194016]If i may humbly suggest instead of openshot try kdenlive

sudo apt-get install kdenlive

it is an awesome program! just install and play with it, i like it much more and it looks more professional[/QUOTE]

---

### Post by houseworkshy on 2012-08-25
It could be that some codecs are missing.  If so then "sudo apt-get install-ubuntu-restricted-extras" may sort things out.  It's a meta package with codecs, flash, some archiveing tools and so on.

---

### Post by dolvita10 on 2012-08-26
atombbomb@photon:~$ sudo apt-get install-ubuntu-restricted-extras
[sudo] password for atombbomb: 
E: Invalid operation install-ubuntu-restricted-extras
atombbomb@photon:~$ 

like I say I&#7743; a beginner what do I do wrong?





> **houseworkshy said:**
> It could be that some codecs are missing.  If so then "sudo apt-get install-ubuntu-restricted-extras" may sort things out.  It's a meta package with codecs, flash, some archiveing tools and so on.

---

### Post by Elfy on 2012-08-26
```
sudo apt-get install ubuntu-restricted-extras
```

You have an extra - :)

---

### Post by codemaniac on 2012-08-26
> **dolvita10 said:**
> hello want to work in terminal whatever I pasted he ask password but he is not reacting , so the cursur is not moving if I give in password?    need this have no audio with preview in openshot      working with ubuntu 12.04  ?   
hope this is the right place to post this?


please help

thanks ,david

On some UNIX-based systems, sudo can show an asterisk (*) when you type your password.

In the terminal, open up /etc/sudoers file in a text editor , e.g. vi.
```
sudo vi /etc/sudoers
```
Now, find the line that reads:
> Defaults env_reset
And replace it with:
> Defaults env_reset,pwfeedback

Finally save and exit the file.


<edit>PS : take a back up of the /etc/sudoers file first .
```
sudo cp /etc/sudoers /etc/sudoers.orig
```
</edit>

---

### Post by houseworkshy on 2012-08-26
> **Elfy said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```You have an extra - :)

 Oppps, sorry about that. my typing mistake; there is no - between the "install" and "ubuntu". Thanks for spotting and pointing it out.

---

### Post by dolvita10 on 2012-08-28
> **houseworkshy said:**
> Oppps, sorry about that. my typing mistake; there is no - between the "install" and "ubuntu". Thanks for spotting and pointing it out.

tatombbomb@photon:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for atombbomb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-zh-hans kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
atombbomb@photon:~$ 


Thanks but seems not nessesary ........   allready newest version still problem with openshot and kdelive  , no sound with openshot,   no possible to put videofiles on the timeline? in kdelive ??

---

### Post by houseworkshy on 2012-08-28
I know you're not getting sound in the video players/editors.  Are you getting audio in any other programs, or online, or hearing system sound effects?
  
If not then try a live session with a distro, it's the "try without changeing your system" option on the Ubuntu distro.  
If that has audio, because most distro's will play their own system sounds and free codecs at least,  then the problem is a software one on the hd install which can be sorted out via the keyboard.  
If not as the software on the cd/dvd should be perfect, being on a write once only media, then it's time to check hardware, connections etc.  

If it is software then boot back into a hard drive session.  First places to look would be the sound preferances, the hardware drivers and the mixer.

---

### Post by dolvita10 on 2012-08-30
Thank you again for asnwering , in other programms I had sound ......but because I followed the instructions on openshot   
[http://openshotusers.com/forum/viewtopic.php?f=12&t=1261](http://openshotusers.com/forum/viewtopic.php?f=12&t=1261)     no sounds at all something to do with python  .get crazy one month searching  notting... quess have to do a clear ubuntu installl   becouse can not get python  uninstall and re-install   

for your information I had a question in forum openshot [https://answers.launchpad.net/openshot/+question/206636](https://answers.launchpad.net/openshot/+question/206636)      does not seems to help because I do not understand all it seems?

could the original problem be something to do with rhythmbox because it looks the only programm what comes up if I press the sound sign (right up the screen?  could it be the back-end of the sound?




QUOTE=houseworkshy;12202986]I know you're not getting sound in the video players/editors.  Are you getting audio in any other programs, or online, or hearing system sound effects?
  
If not then try a live session with a distro, it's the "try without changeing your system" option on the Ubuntu distro.  
If that has audio, because most distro's will play their own system sounds and free codecs at least,  then the problem is a software one on the hd install which can be sorted out via the keyboard.  
If not as the software on the cd/dvd should be perfect, being on a write once only media, then it's time to check hardware, connections etc.  

If it is software then boot back into a hard drive session.  First places to look would be the sound preferances, the hardware drivers and the mixer.[/QUOTE]

---

### Post by houseworkshy on 2012-09-02
My french is minimal.  However it seems that you have installed an  'unofficial' repository.  Repositories are collections of software, the  official ones are checked by the maintainers of whatever distribution  you are using, the unofficial ones are not.  I don't know if this one is  good or not.  I am not saying malware, though that is a risk.  Many if  not most are benign in intention, for example the majority of program  development teams will have one, it will have the latest version but  that version will still be in the process of being written so will have  bugs. It is possible that the one you added is like that and you are up against some bug.

It is actually fairly easy to remove a repository and the programs which  came from it with their associated settings.  What is not so easy is  find out and undo whatever has been done to the system.
As a reinstall only takes half an hour it would probably be faster to  just start again.  All the important unreplaceable things will be in  your home folder so backing that up is quick too.

If you do choose to do this I strongly recomend following this guide as next thing you do 
[https://help.ubuntu.com/](https://help.ubuntu.com/)  
It is more than just a quick guide, it also has within it apt;urls which  are another method of installing packages, so you can learn the basics  and install things which you may need as you go.  Only takes about an  hour to go through the whole thing.

Openshot works ok in 10.04 so you could choose that version of Ubuntu  though it is only supported untill April next year.  Personally I prefer  other video editors.  My own all time favorite is cinelerra cv though I  do have to add an unofficial repository to use it ( you may prefer to  avoid doing that again after this lot. ).  Kdenlive is excellent,  avidimux  and Lives are also good.  If it's only simple PiTiVi, which is on the  default install, is about the same level as openshot.  
Before installing any of them you could have a browse around youtube to  see what you like the look of.  Another reason to look on youtube is  that people have posted tutorial videos on various linux video editors  which is also helpful. 
This one on cinelerra is really well made ( and funny )  [http://www.youtube.com/watch?v=-Q-NTYLiyKc](http://www.youtube.com/watch?v=-Q-NTYLiyKc)
As is this one on kdenlive [http://www.youtube.com/watch?v=1eHEAfNFJ0k](http://www.youtube.com/watch?v=1eHEAfNFJ0k) shows the basics.
Searching +"program name" +tutorial usually pulls a lot.  With graphic software I like to see it done as well as read about it.
There are a lot of choices.

I'd also recomend downloading a copy of this  [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
It's a free pdf and an excellent introduction to the Ubuntu system, definately worth having in ones documents.

So sorry I can't just give a command to paste into the terminal as a  fix, someone may happen by who can, but actually starting again may be  better and faster anyway.  
With any distro I expect to have a few 'finding-things-out' starts  because of things I don't know the first time.  For example, in Ubuntu,  the firewall isn't activated on the default install and I like it to  be.  How many first timers are going to know that?  I didn't. 
For future referance "sudo ufw default deny" will set up good firewall defaults and "sudo ufw enable" will turn the firewall on.

Another really nice feature of Ubuntu is that one can choose desktop enviroments at startup.  A feature you may not need it you have a lot of RAM but if ever your system is pushed,  and rendering *is* heavy on resourses, one can switch to something lightweight such as LXDE for the session.  It's a very simple but good enough to get around GUI which is low on memory and power, many people with mobile devices use it when not plugged in to make the batteries last longer.  
Probably don't bother with alternative GUI's at first, just remember it can easily be done ( a simple install from the software center )  in case your system ever finds some task a bit to big for it.

So not a quick fix but I hope some of the above may be useful.  You've   chosen the right system for video editing.  I used to duel boot with   windows and as some programs are cross platform I'd test them out on   both.  Linux was always very much faster at rendering.

Good luck.

---

