---
title: "Gnome-Do does it. Possibly the most useful desktop application ever.."
date: 2010-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by magozoom on 2010-01-03
[SIZE="5"]A brief introduction to Gnome-Do
[/SIZE]

Gnome-Do must be one of the most useful applications every imagined.
Interacting with the Gnome desktop environment becomes lightning fast, elegant and something that possibly can make Windows 7 and OS X fanatics cry and ask for your Linux LiveCD.

**Do is a different way of getting things done on the computer.** 
It's completely text-based and the power is not obvious at first. 

Gnome-Do comes with an Application dock which is very pretty - but that's not where the real power is.  
If you are like me you spend all day on the mouse left- and right-clicking, launching and dragging windows to get things done and it gets frustrating after a while. 

Ready to change the way you interact with your Linux Gnome desktop forever? Great, here we go!

[SIZE="5"]Installing & running
[/SIZE]
[LIST]
[*]On Ubuntu 9.10 use the **Ubuntu Software Center** and search for Gnome Do. You'll find it in the search results. Click Install. Done.
[*]From terminal with **sudo apt-get install gnome-do**
[*]SUSE, Fedora, Debian... instructions on [http://do.davebsd.com/download.shtml](http://do.davebsd.com/download.shtml)
[*]Build from Launchpad [https://edge.launchpad.net/do](https://edge.launchpad.net/do)
[/LIST]

**Important**: if using Ubuntu Karmic 9.10 with Firefox 3.5 you need to copy the OpenSearch-plugins to your home directory.  Run these two commands to get the web search functionality working. Change "en-US" as appropriate for your language version of Firefox. Use The Help / About Mozilla Firefox menu to see your version, look where is says *Mozilla/5.0 (X11; U; Linux i686; **en-US;** rv:1.9.1.6) Gecko/20091215 Ubuntu/9.10 (karmic) Firefox/3.5.6*

```
mkdir ~/.mozilla/firefox/vkuuxfit.default/searchplugins
cp /usr/lib/firefox-addons/searchplugins/en-US/*.xml ~/.mozilla/firefox/vkuuxfit.default/searchplugins

```

Launch Do from Applications / Accessories menu or run **gnome-do &** from a terminal window. And now...nothing happens!!

You have just turbocharged your Gnome environment and absolutely nothing happens. Until you press **Super + Space** on your keyboard, that is. 

*If my dad is reading this: Super is the key with a little flag  on it,  left of your spacebar. Hold this key and press Spacebar simultaneously. *

**Try it!** You should see this...

[IMG]http://helander.pbworks.com/f/1262462206/Screenshot-Do-trim.png[/IMG]

So far not very exciting, but you're up and running. Let's move on.
 
[SIZE="5"]Basic functionality - Launching applications
[/SIZE]
 
Everyting with Do is accomplished with two keys -  the TAB key and Arrow Down. 

[LIST]
[*]**Arrow Down** chooses between actions suggested by Do. 
[*]**Tab key** confirms.
[/LIST]

Lets see how this works out....

[LIST=1]
[*]Bring up Do by pressing Super + Space
[*]Type "open" and see how Do immediately suggests "OpenOffice.org Word Processor".
[/LIST]
[IMG]http://helander.pbworks.com/f/1262463810/do_open_word_trim.png[/IMG]

If you hit Enter now the Open Office word processor will launch. Wham. Never use the Application menu again!
But what if you wanted OpenOffice.org Spreadsheet? Press Arrow down and you get.... more wham.

[IMG]http://helander.pbworks.com/f/1262463807/do_open_arrow_down_trim.png[/IMG]

Move down in the list of everyting related to "open" (Open Office, Open Terminal, Open File...) until you have OpenOffice.org Spreadsheet selected

Now press TAB. Focus moves to the Run panel. Press Enter. OpenOffice.org Spreadsheet launches. Wham.

You get the idea?  

[LIST=1]
[*]Type a few letters related to what you want to do. Try fire for firefox, cal for calculator, evo for evolution....
[*]If Do suggest the correct application right away you hit Enter and launch the application.
[*]For other alternatives use Arrow Down  - more about how you can control what Do suggests later..
[*]From the drop down list move to actions "launch" panel ("Run") with TAB key, or just hit Enter right away.
[/LIST]

Amazing stuff. But this is really nothing compared to some of the more crazy stuff Do does.

Post to Twitter. Copy Files. Search the web. Search in all you files. Play music. All without ever touching the mouse.

Let's move on...
 
[SIZE="5"]Something with three panels - Web Search.[/SIZE]

Note the fix for Ubuntu 9.10 & Firefox 3.5 above.

[LIST=1]
[*]Bring up Do with the Super & Spacebar combination.
[*]**Type whatever you would like to search for** - we'll use "giant whales".
[/LIST]

Do now suggest Copy to clipboard in the actions panel, but this is not what we want to do. 

[LIST=1]
[*]Press TAB to move to the actions panel, currently displaying "Copy to Clipboard"
[*]Press Arrow Down to choose a different action and select Search Web from the drop down. A third panel now opens where you can choose which search engine to use
[*]By now you know it's TAB to go to the next panel and Arrow Down to choose Google if not already suggested by Do.
[/LIST]

You should see this - most likely with a different desktop background ;)
[IMG]http://helander.pbworks.com/f/1262469586/web_search_whales_step_2_trim.png[/IMG]

Hit Enter to run your search in the web browser.


[SIZE="5"]Configuring Plugins - Twitter[/SIZE]

Gnome-Do comes with a ton of plugins, both Official and Community contributed.
Twitter is one such plugin.

To tweet from Do....

[LIST=1]
[*]Bring up Gnome-Do with the Super-Spacebar combination
[*]Type your tweet up to 160 characters
[*]Press TAB, and choose Twitter from the drop down menu.
[*]Hit Enter and your tweet is posted.
[/LIST]
 
When you have your plugin configured with your username and password you should see this...
[IMG]http://helander.pbworks.com/f/1262470680/twitter_post_step1_trim.png[/IMG]

So. how does one configure the plugins? By default the Ubuntu build of gnome-do does not have an icon in the notification area which we can right-click.  The first time we have to click the little triangle in the Do window to enable the notification icon. Aha, now you see it...
[IMG]http://helander.pbworks.com/f/1262471459/gnome_do_menu_trim.png[/IMG]

Clicking this little triangle we can access the Preferences menu.  In the Preference window you can Show Notification Icon and Start Gnome-do on login on the General Tab, and then move to the Plugins menu. After selecting the Microblogging plugin  you can choose Configure and enter your Twitter login details.

Activate and configure all plugins you want Gnome-do to use. My personal favourites are

[LIST]
[*]Files and Folders - access any document from Do, you can configure which directores that should be indexed and available.
[*]Rythmbox - play any song or album from Do
[*]Skype - initiate Skype calls from Do. It's under the Community plugins drop-down. 
[/LIST]

And some more wicked stuff.. 

[LIST]
[*]If you type a URL, eg [www.nytimes.com](www.nytimes.com), you get the Open URL action and can go straight to the site.
[*]There is an Evolution adress book plugin so you can send an e-mail to Bob by typing "email <TAB> bob" but right now some C# library is broken in Ubuntu, possibly this could work on other distros..
[*]In the Microblogging plugin you can see tweets from people you're following.
[*]If you write something like 45 + 566 -7000 and choose the Google Calculator action, then Do will display the result.
[/LIST]

 
[SIZE="5"]And now for the fancy stuff - an fully integrated Linux Dock, Docky.[/SIZE]

In Gnome-Do's preferences choose the Appearance tab and select theme Docky. Wham.  A fully featured application dock appears.

[LIST]
[*]As you could expect you can drag and drop items from the dock to / from gnome windows.
[*]You can add and remove functionality from the dock in Do's preferences, under Plugins choose Docklets in the drop-down menu.
[*]**To activate Gnome-Do when using Docky** use the familiar Super & Space keyboard combination. Then use TAB and Down Arrow just like before..
[/LIST]

[IMG]http://helander.pbworks.com/f/1262472830/docky_screen_trim.png[/IMG]

Have fun - I hope this introduction  brought you the same smile that I got when I found Gnome-Do!

/Magnus

---

### Post by adeypoop on 2010-01-05
Nice post. 

I can't figure out is why Ubuntu doesn't have this installed by default, it is a fantastically handy tool and much friendlier and faster than navigating through menus with the mouse.

Only problem for me is I'm using Kubuntu at the moment and it doesn't play very well for some reason, had to revert to krunner

---

### Post by tom957 on 2010-01-06
Yeah, Gnome-do pretty much rules.

---

### Post by pt123 on 2010-01-07
with Gnome-Do files and folder plugins, I can get it to index my scripts folder, and run those scripts from Gnome-Do

---

### Post by adeypoop on 2010-01-14
found this link with more info about gnome do

[http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12](http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12)

---

### Post by Tsquad on 2010-01-15
Ok, im stuck with fixing the whole 9.10 and fire fox 3.5 thing. After entering  "mkdir ~/.mozilla/firefox/vkuuxfit.default/searchplugins
" i get an error of "mkdir: cannot create directory `/home/taylor/.mozilla/firefox/vkuuxfit.default/searchplugins': No such file or directory
"

I am able to use gnome do for everything but web browser stuff like the web search function. Anyone know what is causing this?

---

### Post by Shazzner on 2010-01-15
So this is basically Launchy for Linux? Sounds cool I loved Launchy.

---

### Post by Ixtao on 2010-01-15
Like this app more and more! I'd like to know how to activate other themes for docky? Stumbled upon [this one]("http://gnome-look.org/content/show.php?content=117685"). it has a install script but there doesn't seem to be an option to select which theme to use..

---

### Post by magozoom on 2010-01-15
> **Tsquad said:**
> Ok, im stuck with fixing the whole 9.10 and fire fox 3.5 thing. After entering  "mkdir ~/.mozilla/firefox/vkuuxfit.default/searchplugins
" i get an error of "mkdir: cannot create directory `/home/taylor/.mozilla/firefox/vkuuxfit.default/searchplugins': No such file or directory
"

I am able to use gnome do for everything but web browser stuff like the web search function. Anyone know what is causing this?

Try this..
1. Open up your user folder in Nautilus, /home/taylor
2. Press Ctrl-H to reveal hidden folders starting with "."
3. Open to the .mozilla folder
4. Open the firefox folder in the .mozilla folder
5. Find the name of your ".default" folder, possibly it is not "vkuuxfit" as in my case.
6. Now use that foldername, eg "xyxyxy.default" instead when creating the searchplugins directory from the command prompt, as well as when copying the XML files.
7. To hide the hidden folders again press Ctrl-H

/m

---

### Post by ghostier on 2010-04-06
This program is really handy and makes me use my mouse less and less. It completely blew me away when I found out I could simply type in "Mich..." and it would should "Michael" with a chat icon beside it and when I press enter I was directly in a pidgin conversation with my brother.

One thing that brothers me though sometimes when I start it up right after start up it doesn't seem to appear and just crashes my computer after which my computer does not take in any more keyboard input or mouse clicks. I have to reboot everytime that happens (this happens maybe 30% of the time I try to start it up after start up).

---

### Post by mosaabJ on 2010-04-06
Another awsome tool making Ubuntu easier to use, thanks magozoom for the tutorial

---

### Post by treesurf on 2010-04-08
[QUOTE=ghostier;9082197
One thing that brothers me though sometimes when I start it up right after start up it doesn't seem to appear and just crashes my computer after which my computer does not take in any more keyboard input or mouse clicks. I have to reboot everytime that happens (this happens maybe 30% of the time I try to start it up after start up).[/QUOTE]

I have this exact same problem.

---

