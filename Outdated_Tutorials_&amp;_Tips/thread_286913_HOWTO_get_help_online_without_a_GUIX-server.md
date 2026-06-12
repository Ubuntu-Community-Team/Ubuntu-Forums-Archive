---
title: "HOWTO: get help online without a GUI/X-server"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Arby on 2006-10-28
Hi folks,

This is something I put together to get out of a hole on those occasions when for some reason you find yourself lacking an X server. I'm considering putting it in for the wiki/community documentation so I'd appreciate some feedback. It's aimed at inexperienced users so I'd like to know if it's simple enough but doesn't miss anything important. I don't use irssi as an irc client very much so if anyone wants to comment on that section feel free. If anyone wants to try it out and see if it's useable then press CTRL-ALT-F1, press CTRL-ALT-F7 to get back again. There is an obvious issue with having a guide to how to get online that is itself online but I haven't thought of a solution to this yet. Suggestions please.

START
At some point every linux user experiences that sinking feeling when they get dumped at a black and white terminal instead of their pretty graphical login. For new users this can be quite disconcerting, especially if you don't have another computer or another operating system you can boot to search for help. 

This guide is aimed at those new users, it is not intended to fix your broken graphic display but it is intended to show you how to install and use some tools to get online and get some help via the internet without the aid of a graphical browser or irc client.

Getting help via the internet.
In a word: lynx. Lynx is a text based web browser, which means it can be run from the commandline to browse the web. It's homepage is at [http://lynx.browser.org/]("http://lynx.browser.org/").

If you find yourself at a commandline asking you to login enter your usual user name and password. Then if you don't already have lynx installed run this command
```
sudo apt-get install lynx
``` The man page containing detailed instructions on how to use lynx is found by typing ```
man lynx
```

Start lynx by typing ```
lynx
``` Lynx opens at a page containing links to several help guides for lynx. You can return to this page at any time by pressing the m key.

The top link will be highlighted in red, move around the page by using the up/down arrow keys. To follow a link use the right arrow, to go back use the left arrow. When following a link you will often be prompted for input by the browser in the blue box at the bottom.

To go directly to a website by entering it's url press g then enter followed by the address. So to get to google do the following
```
g 
http://www.google.com
Enter
```
You should see a text version of the google homepage. If you find yourself looking at raw xml or html you hit enter too many times, press q to go back. 

Somewhere on the page will be something that looks like this ```
Go______________________
```. Use the up/down arrows until the line turns white. Enter your search terms then hit enter twice. You should see the sponsered links at the top then your search results will be off the bottom of the screen. Use the up/down arrows to scroll through them.

To access the fountain of knowledge that is the ubuntu forums do this:
```
g
http://ubuntuforums.org
Enter
``` To do a search of the forums you should see something that looks like ```
__________________ Search
``` Use the up/down arrows until the line turns white then enter your search terms. Use the down arrow until Search turns red then hit enter. 
*Note*: This can be confusing at first. When the results are returned the top part of the page looks almost identical. The results will be off the bottom of the page, use the arrows to move down.

To post a new question you will need to login. You should see two lines that look like this. ```
User Name UserName_ [ ] remember me?
password ___________ Log In
``` Use the down arrow until you see a blinking cursor next to UserName. Delete this and replace it with your forum user name. Use the down arrow to navigate to the password line. Enter your password and hit enter twice.

Lynx does not automatically redirect you so use the down arrow until the 'click here if your browser does not automatically redirect you' line is highlighted. Hit Enter.

To make a post use the down arrow until the link to your desired forum is highlighted, hit enter. Use the down arrow until 'New Thread' is highlighted, hit enter. The form to enter your question will be off the bottom of the screen, use the down arrow to navigate. There is quite a lot of text to navigate through. This is the text equivalent of the formatting buttons that appear on the graphical window. When you reach the first line of something that looks like this
```
___________________________
___________________________
___________________________
___________________________
``` that's the form, type away. Use the down arrow to find the submit new thread button and hit enter. Question posted, hopefully someone can help you fix that broken graphical display.

Getting help via an irc channel
If your preferred means of getting help is via an irc channel then you can do that from a commandline as well. It is actually much simpler to use than lynx. These commands will get you as far as #ubuntu where hopefully someone can help you.
```
#install irssi
sudo apt-get install irssi
#start irssi
irssi
#connect to irc
/connect irc.freenode.net
#join the hash ubuntu channel
/join #ubuntu
```

THE END

---

### Post by RU-In? on 2006-10-28
Thanks for the tip. Very simple instructions (that work). I am certainly a noob to linux, fortunately not to the text world, I came from the 80's and days of DOS & BBS (300bps/so on). But this is a great tip I could of used this a few times already.

---

### Post by Ocxic on 2006-10-29
You are a saviour my friend..... thank you.

---

