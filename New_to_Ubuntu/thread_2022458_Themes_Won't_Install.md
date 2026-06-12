---
title: "Themes Won't Install"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by DoctorVarney on 2012-07-11
I have the GNOME Tweak Tool (* Advanced Settings *) installed and running in Ubuntu 12.04 and I have created a new folder called* .themes *in the hidden area of the Home folder... as per instructions I've found on this page:

[How To Install GNOME Themes In Ubuntu 11.10 - Softpedia]("http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml")

And I have downloaded - and unpacked with the file archiver -  some themes from this page:

[Download Themes - page 4 - ...Softpedia]("http://linux.softpedia.com/catList/184,0,3,0,4.html")

In the Advanced Settings dialogue, I'm still finding a [COLOR=Sienna]Caution![/COLOR] triangle sign next to the *Shell Theme* pull-down in the Themes section - please see attached image.

While typing this. I've noticed from the page titles that the discussion surrounds version 11.10 and so, naturally, I'm wondering if this has anything to do with the problem.  I would have thought of Ubuntu 12.04 as being backwards compatible.  Is this not the case?  If so, where is a good place to download compatible themes?

Otherwise, does it look to you as though I have followed the installation steps correctly?

---

### Post by stinkeye on 2012-07-11
Change the appearance of your windows with the dropdowns shown in pic.
The shell theme dropdown is for gnome-shell themes when you log in to the gnome session.

---

### Post by tea for one on 2012-07-11
Good morning

Have a browse through the content on this site:-

[http://gnome-look.org/](http://gnome-look.org/)

Ubuntu 12.04 sits on top of Gnome 3.4, therefore you want the 3.4 themes.

I store them in usr/share/themes. You use sudo to move the themes to this folder.

Some themes do not work perfectly so a little caution is required.

Icons can also be stored in usr/share/icons using sudo again.

Good luck

---

### Post by DoctorVarney on 2012-07-11
Update:

I have recently entered the following commands in the Terminal:

[INDENT]
[LIST]
[*][COLOR=red]sudo add-apt-repository ppa:noobslab/gnome[/COLOR]
[*][COLOR=red]sudo apt-get update[/COLOR]
[*][COLOR=red]sudo apt-get install gnome-shell-extensions

[/COLOR]
[/LIST]
[/INDENT]I then "restarted the Gnome Shell" by pressing ***Alt+F2*** and typing '***r***'  as instructed here:
[Important Tweaks/ Things to do After install of Ubuntu 12.04 Precise Pangolin ~]("http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html")

And the result is that the Advanced Settings Shell Extensions tab has changed ( *please see attached image* ) thus.

And I'm STILL completely lost. :(

Why does this have to be SO complicated?! :confused:

---

### Post by DoctorVarney on 2012-07-11
> **tea for one said:**
> Good morning

Have a browse through the content on this site:-

[http://gnome-look.org/](http://gnome-look.org/)

Ubuntu 12.04 sits on top of Gnome 3.4, therefore you want the 3.4 themes.

I store them in usr/share/themes. You use sudo to move the themes to this folder.

Some themes do not work perfectly so a little caution is required.

Icons can also be stored in usr/share/icons using sudo again.

Good luck

Thank you, that's great.  Haven't tried this yet, because I have no idea how to "use sudo".   What commands do I type?

---

### Post by c2tarun on 2012-07-11
If you are still facing problem then please refer to this tutorial [http://www.tricksfind.in/2012/04/how-to-install-new-icons-and-themes-in.html](http://www.tricksfind.in/2012/04/how-to-install-new-icons-and-themes-in.html)

---

### Post by DoctorVarney on 2012-07-11
...And where is "usr/share/themes" ?

---

### Post by DoctorVarney on 2012-07-11
> **c2tarun said:**
> If you are still facing problem then please refer to this tutorial [http://www.tricksfind.in/2012/04/how-to-install-new-icons-and-themes-in.html](http://www.tricksfind.in/2012/04/how-to-install-new-icons-and-themes-in.html)

Thank you!  Reading...

This tutorial offers no additional information to that which I've already explained doesn't work for me.

And what's this...?

[IMG]http://1.bp.blogspot.com/-6SyicUbAros/T4LEjhSeX-I/AAAAAAAAANU/Dwhm_jIEh4U/s400/Screenshot-Appearance%2BPreferences-1.png[/IMG]

It looks nothing like *anything* I see in *my* preferences panel.

---

### Post by DoctorVarney on 2012-07-11
> **stinkeye said:**
> Change the appearance of your windows with the dropdowns shown in pic.
The shell theme dropdown is for gnome-shell themes when you log in to the gnome session.

I know this.  Except, it doesn't change to the themes I have downloaded.  All that does is make the top bar of the windows white.  The theme I chose should be dark grey and looks nothing like it.

---

### Post by DoctorVarney on 2012-07-11
Please can *anyone* give me concise step-step guidance?  All of these tutorials assume the reader is familiar with the terms.  Every time I get an answer to a question, it opens up 20 more questions.

---

### Post by tea for one on 2012-07-11
> **DoctorVarney said:**
> Please can *anyone* give me concise step-step guidance?  All of these tutorials assume the reader is familiar with the terms.  Every time I get an answer to a question, it opens up 20 more questions.

In order to try and provide some clarity, can you confirm if you are using the Unity interface or the Gnome-shell interface?

The default interface for Ubuntu 12.04 is Unity and the Gnome-shell interface has to be added afterwards from the Software Centre.

---

### Post by DoctorVarney on 2012-07-11
> **tea for one said:**
> Good morning

Have a browse through the content on this site:-

[http://gnome-look.org/](http://gnome-look.org/)

Ubuntu 12.04 sits on top of Gnome 3.4, therefore you want the 3.4 themes.

I store them in usr/share/themes. You use sudo to move the themes to this folder.

Some themes do not work perfectly so a little caution is required.

Icons can also be stored in usr/share/icons using sudo again.

Good luck

Nope.  Doesn't work.  Made sure it was a GTK 3.4 theme I downloaded.  Even tried the command the page suggests: [U] 
sudo apt-get installplastiq-gtk-theme[/U] and got back an error message ( which I don't recall )  basically, telling me it couldn't do that.

---

### Post by DoctorVarney on 2012-07-11
> **tea for one said:**
> In order to try and provide some clarity, can you confirm if you are using the Unity interface or the Gnome-shell interface?

The default interface for Ubuntu 12.04 is Unity and the Gnome-shell interface has to be added afterwards from the Software Centre.

Thanks.  Gnome-shell.  I'm pretty sure.  I installed it from the software centre and "Gnome" is the option I use when logging in.  That screen also shows "Gnome Classic" and a few others.  I also have the Gnome Tweak Tool ( which comes up as "Advanced Settings" ).  In the ordinary Display Settings, the themes are not listed there, either.

---

### Post by tea for one on 2012-07-11
Slowly and surely, we will get themes installed for you.....

I agree that it is complicated at the moment because Gnome 3 is fairly new and currently slightly less flexible when you want to change the appearance.

Please confirm that you have installed the following extension:-

[https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

Secondly, please confirm that you have applied the modification to this extension so that it functions with Gnome 3.4

Two separate terminal commands as follows:-

```
sudo cp ~/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com/schemas/org.gnome.shell.extensions.user-theme.gschema.xml /usr/share/glib-2.0/schemas
```

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

These commands were obtained from the user comments within the extension page.

---

### Post by DoctorVarney on 2012-07-11
Cheers! :)

> **tea for one said:**
> 
Please confirm that you have installed the following extension:-

[https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

When I enter the Ubuntu Software Centre, it comes up as installed.

(Edit): When I search for it through the Software Centre, it comes up with "Remove" beneath the name  to suggest it's installed.  But when I look for it amongst the installed stuff, I can't seem to locate it.

> **tea for one said:**
> Secondly, please confirm that you have applied the modification to this extension so that it functions with Gnome 3.4

Two separate terminal commands as follows:-

```
sudo cp ~/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com/schemas/org.gnome.shell.extensions.user-theme.gschema.xml /usr/share/glib-2.0/schemas
``````
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

Just tried that first command and and the Terminal flings back the following error message:

```
cp: cannot stat `/home/varney/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com/schemas/org.gnome.shell.extensions.user-theme.gschema.xml': No such file or directory
```

---

### Post by tea for one on 2012-07-11
Good afternoon

Only the Gnome Shell itself is available from the Software Centre.

Gnome Shell Extensions do not appear there.

You download extensions from this website:-

[https://extensions.gnome.org/](https://extensions.gnome.org/)

Please navigate to this website and click **Installed extensions**. Then, you can see a list of extensions that you have installed on your own system.

I suspect that the command did not work because the extension is not installed.

Back in a few hours.........

Kind regards

---

### Post by DoctorVarney on 2012-07-11
Update:

Well, that's interesting.  I had a theme called 'Elementary Dark' from when I first started playing around with this.  When I tried selected it in some of the element dropdowns -in advanced settimngs (windows shell theme etc) I found things turning colours that I knew were not in that theme, so gave up and came looking here for advice.  I've just managed to change the GTK+  theme to 'Elementary Dark' and got a pleasing result.  So it shows at least something is working.   Though it seems I need to keep the windows shell theme set to the default 'Ambience' theme in order for it not to colour the menu and top bar in white.  I must check now, in case I've made some mistake in remembering what 'Elementary Dark' looked like in the screenshots.

There are other themes I have downloaded.  They appear in the .themes (hidden) folder I made in the Home directory.

But the shell extensions > shell theme pulldown now has 'Default' showing instead of the caution! triangle which was once there.  I'm not sure how to get these other themes into the shell themes pulldown.

I'll keep working on it.

---

### Post by Frogs Hair on 2012-07-11
If you haven't selected an extension PPA , I have had good luck with this one .  [http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html](http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html)

To open usr/share/themes use Alt+F2 or the terminal and type the following. ```
gksudo nautilus
```

Enter the pass word when prompted . When the root file system opens  navigate to File system > usr > share > themes . Root permissions are needed to modify or add contents to the file system hence the command .

Make sure  that all packages are fully extracted or the themes won't work.

---

### Post by tea for one on 2012-07-11
> **DoctorVarney said:**
> Update:

Well, that's interesting.  I had a theme called 'Elementary Dark' from when I first started playing around with this.  When I tried selected it in some of the element dropdowns -in advanced settimngs (windows shell theme etc) I found things turning colours that I knew were not in that theme, so gave up and came looking here for advice.  I've just managed to change the GTK+  theme to 'Elementary Dark' and got a pleasing result.  So it shows at least something is working.   Though it seems I need to keep the windows shell theme set to the default 'Ambience' theme in order for it not to colour the menu and top bar in white.  I must check now, in case I've made some mistake in remembering what 'Elementary Dark' looked like in the screenshots.

There are other themes I have downloaded.  They appear in the .themes (hidden) folder I made in the Home directory.

But the shell extensions > shell theme pulldown now has 'Default' showing instead of the caution! triangle which was once there.  I'm not sure how to get these other themes into the shell themes pulldown.

I'll keep working on it.

Good afternoon

In the advanced setting application, I understand that you have selected Theme, which will give you:-

Shell theme
Window theme
Cursor theme
Keybinding theme
Icon theme
GTK+ theme

Shell themes control the top panel, the favourites on the left and other bits and pieces.

GTK+ themes control colours and appearance when you open applications like Thunderbird, Firefox etc.

You can have separate Shell, Icon and GTK+ themes (please see screenshot)

Some themes are only Shell themes, while others include Shell and GTK+ and many are only GTK+ themes without the Gnome 3 Shell.

The terminology is not perfect and it often exacerbates the efforts to provide solutions.

Have you managed to extract a theme from a downloaded compressed file and place it in /usr/share/themes?

---

### Post by DoctorVarney on 2012-07-11
Oh dear.  I'm afraid this isn't intuitive.  Not you, I mean all of this.  I know you've all done your best to advise me but I can't understand any of it.

---

### Post by tea for one on 2012-07-12
> **DoctorVarney said:**
> Oh dear.  I'm afraid this isn't intuitive.  Not you, I mean all of this.  I know you've all done your best to advise me but I can't understand any of it.

Good morning

Yes, you are correct, it isn't intuitive because Gnome 3 is still being developed. However, it is manageable. The key points to consider are:-

Download and install the desired extensions.
Study the movement of data (i.e. themes) to system folders with elevated (sudo) privileges.
Learn how to extract themes and icons from compresssed files.
Learn how to move the extracted theme folder or icon folder to the location usr/share/themes or usr/share/icons.

Here is a little tip to get started:-

Open Nautilus (i.e. open the file manager)
Hit F3 (for a two pane view)
Click in the right pane
Click File System in the Bookmarks
Your right pane should change and your left pane remains the same
Experiment with navigation to get a feel for the structure

It is the equivalent of having two file managers open but much neater and easier to move files.

If you want to go back to the beginning and start from scratch and double check each modification slowly and surely, then that is fine with me.

I am sure other users will step in and help as we go.

Kind regards

---

### Post by DoctorVarney on 2012-07-12
> **tea for one said:**
> Good morning

Yes, you are correct, it isn't intuitive because Gnome 3 is still being developed. However, it is manageable. The key points to consider are:-

Download and install the desired extensions.
Study the movement of data (i.e. themes) to system folders with elevated (sudo) privileges.
Learn how to extract themes and icons from compresssed files.
Learn how to move the extracted theme folder or icon folder to the location usr/share/themes or usr/share/icons.

Homework assignments!  Yes! Thank you for breaking it down.  The journey is easier when you have a map.  Still, I'd rather put the time and energy in to this than spend any more wrestling with Microsoft Windows.

> **tea for one said:**
> 
Here is a little tip to get started:-

Open Nautilus (i.e. open the file manager)
Hit F3 (for a two pane view)
Click in the right pane
Click File System in the Bookmarks
Your right pane should change and your left pane remains the same
Experiment with navigation to get a feel for the structure

It is the equivalent of having two file managers open but much neater and easier to move files.

Yes!  I discovered that recently.  I've been using this method to transfer files and I love it!

On question - Is there a way of displaying as a tree in the folder navigation pane?  That would be really useful for me.

> **tea for one said:**
> If you want to go back to the beginning and start from scratch and double check each modification slowly and surely, then that is fine with me.


Thank you for you patience.  I'm very glad I joined up here!

----------------------------------------------------------------------------------------------

Next week, I'll have more time to sit down and study.   There is one other thing that is bothering me.  Since implementing the GTK Elemental Dark theme, the entry field text in Facebook and some of the info in the Ubuntu Software Centre is pale grey on white, which is incredibly hard to read.  Is there a short term fix I can use to change the colours of screen fonts?

Edit: I've just installing the GNOME Colour Chooser but that doesn't work.

---

### Post by tea for one on 2012-07-12
> **DoctorVarney said:**
> Since implementing the GTK Elemental Dark theme, the entry field text in Facebook and some of the info in the Ubuntu Software Centre is pale grey on white, which is incredibly hard to read.  Is there a short term fix I can use to change the colours of screen fonts?

Edit: I've just installing the GNOME Colour Chooser but that doesn't work.

Your Elementary theme will control the colours. I have used other themes where the Ubuntu Software centre displays white text on a white background. As I mentioned in previous posts, some themes are less than perfect.

I believe Gnome Colour Chooser used to work with Gnome 2 and doesn't work with Gnome 3.

As another suggestion, if you want to change the desktop appearance, it may be beneficial to download and explore Xubuntu (XFCE interface). [http://xubuntu.org/](http://xubuntu.org/) [http://xubuntu.org/tour/](http://xubuntu.org/tour/)

I do not use Xubuntu myself but I understand that there are many built-in themes and colour choices (easier to change than Gnome Shell). It may be a less steep learning curve than jumping in the deep end with Gnome Shell.

Xubuntu uses the same software resources as Ubuntu so you will not be short of applications.

Best wishes

---

### Post by DoctorVarney on 2012-07-12
Thanks.  If I were to switch to Xubuntu, what would that involve?  Would I have to wipe my hard drive, reformat it and start again?

I like Ubuntu so far but if Xubuntu is more apt for an older system, like the one I'm using, then it might be a good idea.

Thing that I don't like about Linux so far, is the fact everyone has different opinions on how to accomplish things.  All the CLI Terminal commands are different, depending on whom you speak to.  Some people say install to one place, others say somewhere else.   I don't see how I could possibly learn something which has no standard properties or laws to it.  I've even come across a site which tells me to drag a theme package into the display properties window.  Needless to say, that's just science fiction.  At least, it definitely doesn't work.  I didn't even expect it to.

---

### Post by tea for one on 2012-07-12
> **DoctorVarney said:**
> Thanks.  If I were to switch to Xubuntu, what would that involve?  Would I have to wipe my hard drive, reformat it and start again?

Here is my suggestion:-

Dowload the Xubuntu iso.
Burn a "live" CD or create a "live" USB with persistence (assuming your PC allows booting from a USB).
Become familiar with the "live" system.

If you are comfortable with Xubuntu:-

Back up your data.
Double check that you have backed up your data.
The Xubuntu installer is the same as the Ubuntu installer and you can reformat during the installation if required.

If you have difficulty with any of these components, I would suggest a new thread because the topic will be different.

Finally, here are links to a Xubuntu review and a Xubuntu theming exercise where a knowledgeable and experienced user has made a very attractive Xubuntu Desktop.

[http://www.dedoimedo.com/computers/xubuntu-pangolin.html](http://www.dedoimedo.com/computers/xubuntu-pangolin.html)

[http://www.dedoimedo.com/computers/xubuntu-pimp.html](http://www.dedoimedo.com/computers/xubuntu-pimp.html)

Best wishes

---

