---
title: "HOW TO: watch MLBtv on Ubuntu"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by dwdarkstar on 2008-06-24
[COLOR="Red"][FONT="Book Antiqua"][SIZE="3"]This HOW TO has been updated to include the latest version AND the SVN capability, mlbviewer-svn, which is the working version of the program allowing for easy program revisions and updates with out having to reinstall the program.  If you worked this HOW TO previously you will need to work it again to get MLB.tv going on your machine.[/SIZE][/FONT][/COLOR]

[FONT="Book Antiqua"][SIZE="3"]  The following How To was written for the novice user (such as myself) who just wants to be able to use their MLBtv subscription on Ubuntu.  That said, there are most certainly more efficient, or expert, or custom methods for accomplishing the same thing; as well as specific preferences for optimal performance on any individuals machine, you will get none of that here.  This is a BASIC how to which hopefully will get MLBtv going on your machine.

[COLOR="Red"] VERY IMPORTANT: [/COLOR] YOU MUST HAVE AN MLB.tv SUBSCRIPTION FOR THIS TO WORK!!!  THIS MEANS YOU HAVE A USERNAME AND PASSWORD WHICH YOU USE TO LOGIN TO MLBtv.COM!!!  If you do not have an MLBtv account, go there and sign up for a subscription, the cost of service has been doubling annually, but if your a baseball fan, you can't knock the product.

  So now you have an MLBtv subscription with username and password, lets go ahead and get the other stuff you need for this to work.  Open a terminal window.[/SIZE][/FONT]


[FONT="Lucida Console"][SIZE="3"]First update your repositories:[/SIZE][/FONT]
```
sudo apt-get update
```

[FONT="Lucida Console"][SIZE="3"]Next install the latest version of python:[/SIZE][/FONT]
```
sudo apt-get install python
```

[FONT="Lucida Console"][SIZE="3"]Next install simplejson, a specific python script:[/SIZE][/FONT]
```
sudo apt-get install python-simplejson
```

[FONT="Lucida Console"][SIZE="3"]Next install mplayer:[/SIZE][/FONT]
```
sudo apt-get install mplayer
```

[FONT="Lucida Console"][SIZE="3"]Now we need to install mlbviewer, a program written by Jessie Rosenthal to access MLBtv using Linux without a web browser.  Click on the following link:[/SIZE][/FONT]

[SIZE="3"][COLOR="RoyalBlue"][https://sourceforge.net/project/downloading.php?group_id=224512&use_mirror=voxel&filename=mlbviewer-0.1alpha9.tar.gz&a=12700450](https://sourceforge.net/project/downloading.php?group_id=224512&use_mirror=voxel&filename=mlbviewer-0.1alpha9.tar.gz&a=12700450)[/color][/SIZE]

[FONT="Lucida Console"][SIZE="3"]  a new window will open with a download box asking you what to do with the file mlbviewer-0.1alpha9.tar.gz, select save to disk and save it to your desktop.  After the download completes you can close the download manager.  If for some reason the download box does not open for you, simply search sourceforge.net for mlbviewer and download the file that way.

Now go to your desktop directory and unpack mlbviewer:[/SIZE][/FONT]
```
cd Desktop
tar -zxvf mlbviewer-0.1alpha9.tar.gz
```

[FONT="Lucida Console"][SIZE="3"]Next we need to establish the update mechanism to keep your version of mlbviewer current, this is done via small revisions performed by the program administrators and distributed through sourceforge.net. Execute the following commands:[/SIZE][/FONT]
```
sudo svn co https://mlbviewer.svn.sourceforge.net/svnroot/mlbviewer/trunk mlbviewer-svn
cd mlbviewer-svn
sudo python setup.py install
```

[FONT="Lucida Console"][SIZE="3"]It will be a good idea to occasionally update this directory to stay current, and you should subscribe to mlbviewers development thread at [COLOR="Blue"][http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/](http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/)[/COLOR].  Skip to the last page in the thread to view any current revisions.  Additionally you'll receive email alerts when updates are recommended keeping your mlbviewer up to date and keeping you in the game. To update simply type the following:[/SIZE][/FONT]

```
cd mlbviewer-svn
svn up
sudo python setup.py install
```

[FONT="Lucida Console"][SIZE="3"]Now we want to clean things up a bit; move the mlbviewer-0.1alpha9 directory into the mlbviewer-svn directory with the following commands:[/SIZE][/FONT]
```
cd ../
mv mlbviewer-0.1alpha9 mlbviewer-svn
```

[FONT="Lucida Console"][SIZE="3"]Now its time to set up your account information, type the following commands:[/SIZE][/FONT]
```
cd mlbviwer-svn
python mlbviewer.py
```

[FONT="Lucida Console"][SIZE="3"]You should be prompted to hard code your username and password, to accomplish this type the following:[/SIZE][/FONT]
```
sudo gedit ~/.mlb/config
```

[FONT="Lucida Console"][SIZE="3"]  at the top of the page you will see 
[INDENT]user=[/INDENT]
[INDENT]pass=[/INDENT]
  type in your MLB.tv user name and password, for example, if your user name was [email]duncanIdaho@dune.net[/email] and your password was gohla, you would type  
      [INDENT]user= [email]duncanIdaho@dune.net[/email][/INDENT]
      [INDENT]pass= gohla[/INDENT]
  save the file and close it.

Now your ready to watch baseball!  At this point it would be a good idea to read the README file in the mlbviewer-svn directory.[/SIZE][/FONT]  
```
more README
```

[FONT="Lucida Console"][SIZE="3"]To activate mlbviewer and connect to MLBtv type this:[/SIZE][/FONT]
```
python mlbviewer.py
```

[FONT="Lucida Console"][SIZE="3"]  allow a few seconds for the program to connect and login to MLBtv.com after which a list of  todays games will appear; press the "h" key to see a list of hot keys used in the mlbviewer window.  Play ball![/SIZE][/FONT]

[FONT="Book Antiqua"][SIZE="3"]Again, support for mlbviewer as well as additional information, including the ongoing development thread pertaining to the topic of MLBtv on Linux, can be found at the following links:[/SIZE][/FONT]

[SIZE="3"][COLOR="RoyalBlue"][http://sourceforge.net/project/shownotes.php?release_id=611172&group_id=224512](http://sourceforge.net/project/shownotes.php?release_id=611172&group_id=224512)

[http://www.eds.org/~straycat/mlblinux.php](http://www.eds.org/~straycat/mlblinux.php)

[http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/](http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/)[/COLOR][/SIZE]

[SIZE="3"]If you enjoy the program and would like to say "Thanks", direct it to the following email address:
[email]jesse.k.rosenthal@gmail.com[/email][/SIZE]

---

### Post by fetzkom on 2008-06-24
Hey, I followed all the steps, but couldn't get it to work. I got all the way down to:

[I][B][I]Next hard code your username and password:
Code:

sudo gedit ~/.mlb/config

at the top of the page you will see

    user=

    pass=[/I][/B][/I]

I never got to see any user or password and then it said it couldn't find the file directory. Ugh. I guess I'm less than a novice! Thanks for any help.

---

### Post by dwdarkstar on 2008-06-25
[FONT="Book Antiqua"][SIZE="3"]Hey fetzkom,  did every thing else install properly? No errors anywhere?  What version of Ubuntu are you running?  Try this:

go into the mlbviewer directory and type[/SIZE][/FONT]
```
python mlbviewer.py
```

[SIZE="3"][FONT="Book Antiqua"]It should prompt you to hard code your username and password, if it does then proceed with:[/FONT][/SIZE]
```
sudo gedit ~/.mlb/config
```

[FONT="Book Antiqua"][SIZE="3"]Let me know if it works out.  If so I'll have to add that step to the HowTo[/SIZE][/FONT]

```

```

---

### Post by fetzkom on 2008-06-27
It seemed to work...The step did take me to the user and password prompt. I then was able to load the MLB Viewer. I clicked on an archived game and audio started to play flawlessly. But, no video. I exited, and when I typed the prompt again, it said it couldn't find the folders/files. If only I could get MLB TV and my Zune (that's a whole other issue!) to work, I wouldn't need no stinking Windows!

---

### Post by dwdarkstar on 2008-06-27
Thanxs for getting back to me fetzkom; so you had it working with audio and then it stopped working?  Hmmm...  well I know I'll have to add that intermediate step which then prompts for a username and password, but your particular issues don't make sense.  Though its most certainly not the case, my only reaction is that your mistyping the terminal commands.  Once you have the mlbviewer open, just highlight any avaliable game and hit ENTER, mplayer will open and begin buffering the stream, followed by a separate window containing the video fed.  Thats it.  No fuss, if your system is not fast enough to support the streaming video (like mine is), mplayer will tell you.  And I have to say fetzkom that if you typed: *python mlbviewer.py* and it opened mlbviewer the first time, it will work again; remember though that you MUST be in the mlbviewer directory to execute that command right?  You can't be in your home directory and expect that command to work.  Let me know if you get it straight.  Thanxs for your reply.

---

### Post by fetzkom on 2008-06-27
It seems to be telling me I can't get video because my video card does not offer xvid support. I was able to get audio going again. So close, yet so far away. Any thoughts?

---

### Post by dwdarkstar on 2008-06-28
Actually fetzkom, I can only use the audio feature as well because my system is to slow, but I don't mind as I enjoy listening to the games while I'm doing other stuff.  As far as the xvid support I don't know much but your certainly in the right place to find out.  I would google it to find out what exactly xvid is and then use the forums to figure out how to fix it.  Sorry I can't be of more help but I'm glad you got the audio working!  Keep struggling though as it is a great way to learn.  Good Luck!

---

### Post by byrong on 2008-07-18
Long story short.  I'm a newbie to Linux.  I don't know what all i did but I actually got my MLB gameday audio to work in Firefox.  I'm not sure if I did anything after that but one day, (in the last week), it stopped working.  I fried firefox trying to get it to work again so I had to reinstall Ubuntu.  Then I couldn't get MLB to work again so I thought I'd try mlbviewer.  Thanks to your great directions I got it running to a point.  I even have a launcher setup for it which I was happy to get working.  Anyway, the problem is:  I launch mlbviewer.  It sees the games.  I select one and press "a" for audio.  It thinks for awhile then I get: 

An error occurred in locating the game stream:

Receiving concurrent use error. :-(:'NoneType' object has no attribute 'groups'

I've checked my login and password.  The only thing I have different is I have it located in a different directory than desktop.  Would that be a problem?

Thanks for the help.

---

### Post by daftcat on 2008-07-18
> **byrong said:**
> Long story short.  I'm a newbie to Linux.  I don't know what all i did but I actually got my MLB gameday audio to work in Firefox.  I'm not sure if I did anything after that but one day, (in the last week), it stopped working.  I fried firefox trying to get it to work again so I had to reinstall Ubuntu.  Then I couldn't get MLB to work again so I thought I'd try mlbviewer.  Thanks to your great directions I got it running to a point.  I even have a launcher setup for it which I was happy to get working.  Anyway, the problem is:  I launch mlbviewer.  It sees the games.  I select one and press "a" for audio.  It thinks for awhile then I get: 

An error occurred in locating the game stream:

Receiving concurrent use error. :-(:'NoneType' object has no attribute 'groups'

I've checked my login and password.  The only thing I have different is I have it located in a different directory than desktop.  Would that be a problem?

Thanks for the help.

Concurrent use error...hmmm, that looks more cryptic now that I see it on someone else's screen. 

When we first wrote the code, mlb.tv was having really tough problems tracking users and making sure they weren't sharing their account with their friends.  They ended up snagging a lot more people who were fairly using the service on their own machines.  This was happening so frequently, that I rewrote the network code to be almost obsessive about logging in and logging out before and after each request and not trusting the cookie to be valid across requests.

Sometimes it still shows up but it's usually a temporary error.  There are several others that are like that like "Login unsuccessful" or "Logout unsuccessful."  Most of these are mlb.com's problems and not mlbviewer.  

The best course is that if you run into an error, try again.  If you keep running into errors, enable debugging by pressing 'd' which will dump the contents of all web pages received from mlb.com to the log file in ~/.mlb/log (and probably crash mlbviewer too.)  That's okay because I wanted to bypass the normal code that catches errors to see the errors when debugging is enabled.

If after trying again and trying again with debug enabled, you can send the log to me or post it here:
[http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/page53.html](http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/page53.html)

Don't be afraid of how big that thread is.  I get notified whenever someone adds to it and there are a few users who also respond on that thread to.  As soon as I get Forum Administrator permissions from the original developer, I'll set up the Sourceforge forum to be more welcoming for questions and support, but you can post there too.

Cheers!
daftcat

---

### Post by daftcat on 2008-07-18
Thank you dwdarkstar for your instructions.  I might have to steal them for the documentation. ;-)

Cheers,
daftcat

---

### Post by byrong on 2008-07-18
I did the debug and it did crash.  Then I played a video I downloaded for my kids with mplayer.  Thought I'd try it again and it got passed that point but gave me a bunch of errors in mplayer.  Was trying it while doing a download so I thought I'd try it again with full 256 bandwidth!! LOL Anyway, that's all I did and it works now.  I can't believe it!  Very excited,  Thank you so much for the post.  I've had several startup issues with getting linux on my machine to work but have found the answers on this or other linux forums.  The support is great and what makes the product.  Very happy to be in it.  Linux rocks. 

Great program.  All I have to do is click on my launcher with the mlb logo, select the game and let her go.  Much faster and less cumbersome than going through mlb site.  Thanks again!

---

### Post by dwdarkstar on 2008-07-20
[SIZE="2"] Glad to hear its working for you byrong!  And you are quite correct, Linux does rock, and support networks like Ubuntuforums are great places to get answers.  As you spend more of your computing time in a Linux environment you will encounter various hurdles which can be frustrating; but with a little research and persistence you can often overcome these issues on your own.  Versus a PC platform where your options are basically REBOOT or purchase an upgrade.  

  The real beauty of Linux though is that anyone has the power to improve upon it by writing programs and sharing them as solutions to common problems.  Mlbviewer is a great example of this; Microsoft bought the front door access to MLBtv, so jkr made a key to the back door!  And then made it available to all of us, free of charge, AND with support; thats the difference.  Spread the word, "Join the Revolution, Support the Evolution, Computing the Future with Linux"

  And by all means Daftcat, take what you like, we've all taken mlbviewer!  Thanxs for continuing a great program.  I'll try to keep the How-To current with releases ect, but your advice is always welcome in the thread.  Thanxs again! =D>

dwdarkstar[/SIZE]

---

### Post by daftcat on 2008-07-21
Credit should go where credit is due.

(Why do I feel an acceptance speech coming on? ;) )

Jesse Rosenthal aka jkr on the LinuxQuestions.org thread was actually the primary developer who figured out the back door and picked its lock (so to speak.)  As documented by the first several pages in that thread, there was a lot of others who found bits and pieces of the puzzle who helped contribute to the knowledge.  Finally, there are a lot of users who gave us feedback on what works and even more importantly, what didn't work (though we often like hearing the first kind of feedback better) to help us improve mlbviewer.  Without the feedback of the user community, it wouldn't have gone nearly as well as it has.  I'm also eternally grateful to the ones who take time to help others with mlbviewer, who have no code investment but share the wealth and experience out of kindness and appreciation of the Linux spirit.

For my part, I took Jesse's initial code and slowly (at first) hacked in little things I wanted and shared with Jesse and the community.  I helped him rewrite the network code when the concurrent login issue was biting a lot of people in the butt.  Eventually, Jesse's school obligations got the better of his time and I took over support and new development.  I still think of him as the engine designer, while I've added a lot of paint to the body (and maybe a couple of things under the hood.)  

Jesse's email address is in the setup.py file and I'm sure he'd get a kick out of a 'thank you' since it seems like I'm getting more than my fair share of credit these days.

Cheers!
Daftcat, mlbviewer jr developer

---

### Post by okdok on 2008-08-02
Kudos to all who participated on this project! :popcorn:

Running the following:

Hardy 8.04
Nvidia Quadro FX 1600
Intel Core Duo T7800 2.7
4g Ram

I followed these instructions and the install was flawless. I was able to get video; albeit with a green strip down the left side. (Any clues?)

Audio works well too! 

Many thanks again! I am sooooo happy to be able to run my mlb.com games w/out running windoze in virtual box to see my games. 

If I could only solve the green line.......:)

---

### Post by drs305 on 2008-08-02
I'm listening to MLB audio at this very moment. For those that might be tempted to see what MLB Video is all about, there is currently a free 5-day trial available. ;-) You can follow the above instructions and see if the setup works for you.

I've self-reported this to the mods in case they decide it's too close to a commercial endorsement...

---

### Post by dwdarkstar on 2008-08-02
[SIZE="2"]Hey okdok, glad to hear the install worked for you!  But the green line issue is certainly odd and something I have not yet experienced.  However my first thought is that it probably has something to do with the mplayer and not mlbviewer or mlbtv.com.  I would check the default screen resolution for your machine, and then make sure that the resolution setting for mplayer does not exceed this.  Be aware however that sometimes the video feeds from mlbtv.com will be framed by this annoying black border that persists even in full screen mode, but in between innings the commercials will be wide screen?  So basically the video can be a bit buggy.  But a green stripe sounds to me like filler space resulting from screen resolutions being mismatched.  You'll have to google around to find your machines resolution settings, but mplayers configurations can be located with the following commands:  [/SIZE]

```
cd /etc/mplayer
sudo gedit mplayer.conf
```

[SIZE="2"]Let me know if you get it fixed, Good Luck![/SIZE]

---

### Post by puyanera on 2008-08-04
Wow, i've only been on ubuntu a few days but this is the first tutorial i've managed to get to work first time.

Thanks for the help dwdarkstar

---

### Post by dwdarkstar on 2008-08-04
Your quite welcome puyanera.  If you enjoy mlbviewer be sure to send a thanks to the developers!

---

### Post by chris86wm on 2008-08-08
I followed the guide and was able to get audio going through mplayer but I didnt have video.

To fix this I changed the "video_player=" section of the config file to
```
video_player=vlc
```

Not sure why video works in VLC and not Mplayer for me but I thought this might help somebody.
Cheers and thanks for the guide. MLB.tv is working flawlessly for me :)

---

### Post by okdok on 2008-08-11
Does anybody know how to select the preferred audio broadcast for a game?

i.e. MLB offers the option to select either the Home or Away broadcast in the audio section.

I'm not too fond of listening the the away team broadcasters. :lolflag:

---

### Post by dwdarkstar on 2008-08-11
[SIZE="2"]Hey okdok, you must hard code the team you wish to follow in the mlbviewer configuration file.  Before that you must identify your teams program abbreviation in the README file located in the mlbviewer directory you created during the install.  Follow these steps: 
1. Go to your mlbviewer directory and type the following code[/SIZE]
```
more README
```
Scroll down by pressing enter until you see a list of team abbreviations, identify your team, then press the "q" button on your keyboard.
2. Next type this
```
sudo gedit ~/.mlb/config
```
Scroll down and find the line that reads audio_follow = x, delete "x" and type your teams abbreviation.  Save the changes, your audio will now be the home broadcasters.

---

### Post by okdok on 2008-08-13
:lolflag: usually i read the README files... heh. this time i overlooked it.

Thanks for the tip, worked like a charm!

---

### Post by jlambeth1 on 2008-08-16
This tutorial is the best one I have used in a while. This now leaves me with only a couple of other things that I need to work out in Ubuntu to be completely free of Microsoft.  One question, any way I can create some type of desktop shortcut to start this up rather than going to a terminal every time?  Thanks to everyone involved in this project.

---

### Post by dwdarkstar on 2008-08-17
Hey jlambeth1, i'm glad you found the tutorial to be helpful.  The answer to your question is that mlbviewer is a terminal run program, and I don't know of any gui versions.  However you can grant mlbviewer system wide access by navigating to you mlbviewer directory and typing the following code:
```
python setup.py install
cp mlbviewer.py ../mlb.tv
```  (The name "mlb.tv" is arbitrary, you can call it whatever you want)
This way, when you want to watch a game, just double click the mlb.tv script icon on your Desktop and a question window will pop up asking if you want to "run mlbviewer.py or display its contents", click 'Run in Terminal' and a terminal window will automatically open displaying the current listings.  Not a gui interface, but a bit of a shortcut none the less.  Hope this helps!  And keep working to break those PC chains, you'll be better for it!

---

### Post by jlambeth1 on 2008-08-18
Thanks for the tip.  A script icon will work great for me.  I see you have your location as Alaska.  I spent 15 years in Fairbanks and still have some family up there.  It's great to still that linux use is reaching the great white north.

---

### Post by devcon101 on 2008-09-26
I know this thread is rather old, but I just ordered the playoff package. I just wanted to note how I got it to work.

I am using:

Hardy 32bit
Opera
Flash 10 RC
Mplayer Plugin

I simply installed the flash and mplayer plugins into my opera plugins directory.  Afterwards, my mlb.tv streams loaded right up.  Oddly it does not work with Firefox.  

Anyway, I will probably try this tutorial too, but here is another option for you folks.

---

### Post by uchuunoyanushi on 2009-03-05
Opera worked for me as well. I already had the mplayer plugin and Flash 10 installed for Firefox, so there was no need to reinstall into the Opera plugin directory.

Thanks for the tip devcon!  Been wanting to try Opera, this just gave me a good excuse. =P

---

### Post by xirrin on 2009-03-14
Followed the instructions and this is what I get...

```
ethan@ewhbuntu:~/Desktop/mlbviewer-0.1alpha7$ python mlbviewer.py
Traceback (most recent call last):
  File "mlbviewer.py", line 704, in <module>
    curses.wrapper(mainloop, mycfg.data)
  File "/usr/lib/python2.5/curses/wrapper.py", line 44, in wrapper
    return func(stdscr, *args, **kwds)
  File "mlbviewer.py", line 154, in mainloop
    available = mysched.getListings(cfg['speed'],cfg['blackout'],cfg['audio_follow'])
  File "/home/ethan/Desktop/mlbviewer-0.1alpha7/MLBviewer/mlbtv.py", line 334, in getListings
    listings = self.trimList()
  File "/home/ethan/Desktop/mlbviewer-0.1alpha7/MLBviewer/mlbtv.py", line 247, in trimList
    ' at ' +\
KeyError: u't878'
ethan@ewhbuntu:~/Desktop/mlbviewer-0.1alpha7$ 

```


Any suggestions? MLB.TV and my video card are the only things left that keep me from cutting the cord on windows :(

---

### Post by dwdarkstar on 2009-03-15
[SIZE="3"]Hey Xirrin,

  OK, so I'm getting the exact same error message today, which is very odd seeing as yesterday I was listening to Yankees at Red Sox... so I have a feeling that MLB.TV has altered something in their login criteria which is causing mlbviewer to bugout.  This happened once before last season and it required an update to mlbviewer.  Let me shoot an email to Daftcat and see if he has any ideas.  May not get fixed immediatley but keep an eye on this thread for updates.  Either way its not you or your machine so sit tight.  Thanxs,

dwdarkstar[/SIZE]

---

### Post by dwdarkstar on 2009-03-15
[SIZE="3"][COLOR="Red"]IMPORTANT UPDATE[/COLOR][COLOR="Black"]

  Alright, Xirrin there is a new version of mlbviewer out: [COLOR="Blue"]mlbviewer-0.1alpha8[/COLOR], i've updated the original instructions so you'll have to do them over agian, sorry.  [/COLOR][/SIZE]

_[SIZE="4"][COLOR="Red"]ALSO[/COLOR][/SIZE]_
[COLOR="Black"][SIZE="3"]If you run into bugs now and throughout the season, chances are your not the only one and there is a way to update your version of mlbviewer via sourceforge.net by command line for bug work-arounds.  This mehtod is detailed in the README file and the execution code is as follows:[/SIZE][/COLOR]
```
sudo apt-get install subversion
sudo svn co https://mlbviewer.svn.sourceforge.net/svnroot/mlbviewer/trunk mlbviewer
sudo python setup.py install

```

 I'm currently working on an issue reguarding the game listings page and will post again when I figure out whats going on.

---

### Post by xirrin on 2009-03-16
Thanks dw! I got it to open, but see the error with the listings page that you were talking about. I appreciate the help, and nice job with the updates! This made my evening :)

---

### Post by dwdarkstar on 2009-03-16
[SIZE="3"]Great xirrin, so sit tight as i'm currently nagging Daftcat about the parsing error.  Do me a favor and type the following code from within your mlbviewer directory and then post the output onto this thread.  Thanxs,

```
python mlblistings.py
```[/SIZE]

---

### Post by daftcat on 2009-03-16
> **dwdarkstar said:**
> [SIZE="3"][COLOR="Red"]IMPORTANT UPDATE[/COLOR][COLOR="Black"]

  Alright, Xirrin there is a new version of mlbviewer out: [COLOR="Blue"]mlbviewer-0.1alpha8[/COLOR], i've updated the original instructions so you'll have to do them over agian, sorry.  [/COLOR][/SIZE]

_[SIZE="4"][COLOR="Red"]ALSO[/COLOR][/SIZE]_
[COLOR="Black"][SIZE="3"]If you run into bugs now and throughout the season, chances are your not the only one and there is a way to update your version of mlbviewer via sourceforge.net by command line for bug work-arounds.  This mehtod is detailed in the README file and the execution code is as follows:[/SIZE][/COLOR]
```
sudo apt-get install subversion
sudo svn co https://mlbviewer.svn.sourceforge.net/svnroot/mlbviewer/trunk mlbviewer
sudo python setup.py install

```

 I'm currently working on an issue reguarding the game listings page and will post again when I figure out whats going on.

According to the instruction above, you have installed the svn version as a subdirectory within the official version. I wouldn't recommend this. A quick and easy fix is to:

```

mv mlbviewer ../mlbviewer-svn
cd ../mlbviewer-svn
sudo python setup.py install 

```

A better way to do this is to understand the svn co command and use it correctly the first time.  svn co takes two arguments: the location of the svn repository (that url portion) and where you want to save/what you want to call the checked out code.  Since you performed this within the release directory, you saved it as a subdirectory in the release directory.

Instead, you should cd out of your release directory and perform a checkout command like:

```

sudo svn co https://mlbviewer.svn.sourceforge.net/svnroot/mlbviewer/trunk mlbviewer-svn
cd mlbviewer-svn
sudo python setup.py install

```

By the way, if you have ever run the setup.py, you will have to run it every time you update from svn.  Once you have checked out from svn, you shouldn't need to check out again.  You can perform an update like:

```

cd mlbviewer-svn
svn up

```

How can you tell when a new revision is available?  Well, you can run the svn up occasionally, or you can subscribe to the linuxquestions.org thread where I post regular updates whenever I've checked something into svn that I believe you should update to.  That thread is here:

[http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/](http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/)

Don't worry that it's 65 pages long.  Just skip to the last page.  We're all aware of how very long that thread is but we're also all subscribed to the thread so we get emails telling us when new replies have been posted.

---

### Post by daftcat on 2009-03-17
> **dwdarkstar said:**
> [FONT="Book Antiqua"][SIZE="3"]  

```
cd mlbviewer-svn
svn up
```

[FONT="Lucida Console"][SIZE="3"]Now go back into the newly created mlbviewer directory, and then type the command below:[/SIZE][/FONT]
```
cd mlbviewer-0.1alpha8
python mlbviewer.py
```



Almost right.  Once you've updated via svn you'll want to continue to use that directory.  You don't want to go back to the 0.1alpha8 directory (or whatever official release you downloaded) because you'll be using the older code.  You don't want to mix and match the directories.  In fact, once you've decided to use the svn, you can pretty much ditch the official releases.  

The official releases are just snapshots of the svn revisions. For example, 0.1alpha9 will be released soon and it will be based off svn revision 115.  Therefore if you have updated to svn revision 115, you already have 0.1alpha9 and you won't need to download the official release.

You could update to svn revision 116 coming on the heels of 0.1alpha9 just to get the version string increased to 0.1alpha9svn vs. 0.1alpha8svn.  That will be the only difference between revision 115, revision 116, and 0.1alpha9 (the official release.)

The other thing to note is that if you have ever run the setup.py whether in the official release directory (such as 0.1alpha*) or the svn directory (mlbviewer-svn), you will have to run the setup.py every time you update even with svn to insure that the correct library files and mlbviewer.py executable is being used.

---

### Post by daftcat on 2009-03-17
You can think of the relationship between the official releases and the svn revisions like Windows Service Packs vs. Windows Update non-critical fixes.  

Generally, if there is a bug that causes mlbviewer to stop working, I'll cut a new official release so that new users don't have broken code from the initial download.  Spring Training this year was an exception.  I wanted to see what else MLB.com might break on Opening Day before cutting a new release.  However, I will be releasing the fix for the listings issue noted this weekend as 0.1alpha9 in the next day or two.

As for the svn revisions, they contain both minor, non-critical fixes, and new features under test.  For example, there is a new script in the svn repository that I'm not ready to package in the official release.  So those who want to test new functionality or get minor, non-critical fixes, you can subscribe to the linuxquestions.org thread and get notified of new revisions.

But as I said in the previous post, once you start updating via svn, you should not mix svn with official releases.  You can always go back to an official release if you decide the svn revision isn't working for you. But you should always run the setup.py script or run the mlbviewer.py from the code version you want to use whether that's the official release or the svn revision.  In other words, you can't install an svn revision (using the setup.py) and use the official release mlbviewer.py (or vice versa.)

---

### Post by daftcat on 2009-03-18
For those who are confused by or scared of SVN, I released 0.1alpha9 last night which has the listings and parser problem fixes that have been reported recently.  There are also media availability indicators for Spring Training which is useful since not all games are covered (no audio, no video, or no media.)

You should be able to watch the remainder of Spring Training and the WBC with 0.1alpha9.

You won't however get any better than 600K until the regular season starts.  The quality will go up to 800K but any higher than that, you'll need the flash player for.  They've chosen to implement speed throttling some in the flash player but most in the nexdef plugin which mlbviewer will likely not be able to support on linux.

By the way, if anyone has Mac OS X, can you send me the nexdef .dmg file so I can see if there's any java code we can use in linux?  Tried just the autobahn code and it was a no go.

---

### Post by xirrin on 2009-03-20
> **daftcat said:**
> For those who are confused by or scared of SVN, I released 0.1alpha9 last night which has the listings and parser problem fixes that have been reported recently.  There are also media availability indicators for Spring Training which is useful since not all games are covered (no audio, no video, or no media.)

You should be able to watch the remainder of Spring Training and the WBC with 0.1alpha9.

You won't however get any better than 600K until the regular season starts.  The quality will go up to 800K but any higher than that, you'll need the flash player for.  They've chosen to implement speed throttling some in the flash player but most in the nexdef plugin which mlbviewer will likely not be able to support on linux.

By the way, if anyone has Mac OS X, can you send me the nexdef .dmg file so I can see if there's any java code we can use in linux?  Tried just the autobahn code and it was a no go.


Are you talking about the player thats available through the mlb.com website?

---

### Post by jdeslip on 2009-04-14
Hello.  I was thinking about paying for mlb.tv, but am a bit confused by this?  Does the streaming flash from mlb.com not work in linux/firefox?  I clicked on a test game and it seemed to work fine (for my free 116 seconds).  Why do you need this mlbviewer program?

---

### Post by orethrius on 2009-04-15
> **jdeslip said:**
> Hello.  I was thinking about paying for mlb.tv, but am a bit confused by this?  Does the streaming flash from mlb.com not work in linux/firefox?  I clicked on a test game and it seemed to work fine (for my free 116 seconds).  Why do you need this mlbviewer program?
I think the point is that this works *separately* from any browser, so MLB broadcasts can be viewed (for instance) from a MythTV / Mythbuntu media PC.

---

### Post by dwdarkstar on 2009-04-15
hey jdeslip,

  yeah so this year MLB.TV has gone with an Adoboe Flash player based system which works with Linux; however all previous seasons have been Windows based Media players and this required a custom program, called mlbviewer, to allow Linux users to make use of their MLB.TV subscriptions.  Some people still want to use mlbviewer, and if your one of them I would recommend you vist the development thread avaliable at Linuxquestions.org given on page one of this How To thread.

---

### Post by daftcat on 2009-05-26
It's been awhile since this HOWTO has been updated.  In fact, it's pretty much out-of-date for the 2009 season.

The Flash player does work with Linux though many mlbviewer users have reported better performance using mlbviewer combined with the latest mplayer code.  Also, mlbviewer supports NexDef this year and full 3000K stream support.

Please download the latest release (0.1alpha11) from sourceforge or use the SVN instructions earlier in this thread to check out the latest svn revision.  Then, you must follow the instructions in the REQUIREMENTS-2009.txt file in the mlbviewer directory rather than using this HOWTO.

---

