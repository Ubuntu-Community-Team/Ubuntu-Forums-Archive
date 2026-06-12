---
title: "How To Add Custom Functionality To Nautilus"
date: 2009-02-02
forum: Outdated Tutorials &amp; Tips
---

### Post by guriman on 2009-02-02
Nautilus, as you know, is the default file manager for Gnome Desktop Environment. It&#8217;s where you wander and spend most of your time, when you are not browsing the web or firing commands at the command prompt.

So obviously it would be cool and productive to some tools that make your work easier. Nautilus actions allow you to add custom functionality to Nautilus. This is achieved via the right click menu. You can inter-convert files in various formats, mount ISO files, merge PDF files all from within Mautilus without launching any other application all from the right click context menu. The possibilities here are only limited by your imagination!

Adding such custom functionality is pretty easy. You don&#8217;t need to be a Linux hacker or programmer to get it working. All you need is:

    * The &#8216;nautilus-actions&#8217; package
    * The knowledge of an equivalent command to achieve the same objective

**The Nautilus-Actions Package**

The nautilus-actions package is what provides you with a nice graphical tool where you can create, edit and remove nautilus-actions or the custom functionality we are looking for. It is easily available through your distribution&#8217;s package manager.
Knowledge Of The Command

As a Linux user you are no stranger to the fact that most of the tasks that you perform via the mouse and GUI can be accomplished via commands as well. Want to print resume.doc? Just enter &#8216;oowriter -p resume.doc&#8217; in the terminal. Need to convert a jpeg file to gif? Enter &#8216;convert logo.jpeg logo.gif&#8217; (requires imagemagick). Want to set an image as wallpaper? Type ```
gconftool-2 -t str &#8211;set /desktop/gnome/background/picture_filename
```
So you can achieve almost anything from the command line and this is what we will exploit here.
[B]
Create An Action[/B]

Let me illustrate the steps you need to follow with an example. We will create a nautilus action to convert flv files to mp4 suitable for playback in an iPod Touch/iPhone. I will use ffmpeg for conversion, so make sure you have it installed (mostly available through package managers, &#8217;sudo apt-get install ffmpeg&#8217; on ubuntu) if you plan to use the action or try along.

    * Go to System > Preferences > Nautilus Actions

[IMG]http://www.makeuseof.com/wp-content/uploads/2009/01/initialnact.png[/IMG]

    **Click on Add. (Note that you can edit, remove, import/export actions from here on in)

[IMG]http://www.makeuseof.com/wp-content/uploads/2009/01/optionsnact.png[/IMG]

* In the label field, type the text you want to appear in the right click context menu of flv files. You can choose an icon and specify a tooltip which provides information about what this option would do. I will skip both of these as they are not essential for functionality.

* Path and Parameters is where all the action is. In path put in the utility that you will use to perform the action. We will be using ffmpeg so put in /usr/bin/ffmpeg here. If you are not sure where the utility resides use the &#8216;where is&#8217; command to find out. eg use &#8216;whereis ffmpeg&#8216; to know its location.

* The parameter line is going to be scary so hold your breath and copy paste:```
-i %d/%f -f mp4 -vcodec libxvid -maxrate 01000 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -s 480×320 -ab 0128000 -b 400000 %d/%f.mp4
``` Don&#8217;t blame me, this is what you need to enter on the command line to convert flv to mp4 with ffmpeg (refer man ffmpeg for more details)! What is noteworthy is the %d and %f. These two provide information on which file you right clicked. Click on the legend button for more details. By the way, I am no video expert and I don&#8217;t claim the options above to be perfect, it does the job just fine. So if you have some suggestions please feel free to share them in comments. 

[IMG]http://www.makeuseof.com/wp-content/uploads/2009/01/conditionsnact.png[/IMG]

*Next click on the condition tab.  This is where you will limit your options to the context menu&#8217;s required file types (flv in our case). You can limit your choices via the filename metacharacters or via the mimetype. Additionally you can specify if your action appears for files only or for files and folders as well. We will type &#8216;*.flv&#8217; for filename and apply our actions to files only.

[IMG]http://www.makeuseof.com/wp-content/uploads/2009/01/advancedcondnact.png[/IMG]

* In the advanced condition tab, you can further limit your choice to local files, samba shares, ftp files etc. We will choose local files here.
* Click OK and you are done!

[IMG]http://www.makeuseof.com/wp-content/uploads/2009/01/menunact.png[/IMG]

Now go look for an flv file. Right click and presto, there is your very own custom &#8216;Convert for iPod&#8217; option. Click on it and you will see a new mp4 file in the same folder.

[IMG]http://www.makeuseof.com/wp-content/uploads/2009/01/bothnact.png[/IMG]

---

