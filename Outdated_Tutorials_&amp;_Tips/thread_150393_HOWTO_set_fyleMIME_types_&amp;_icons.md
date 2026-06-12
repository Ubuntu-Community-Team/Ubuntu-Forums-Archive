---
title: "HOWTO: set fyle/MIME types &amp; icons"
date: 2006-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by andbelo on 2006-03-25
This HOWTO describes how to set the *File* and *MIME* type of files **manually** and also how to associated MIME icons to specific types of files.

In this HOWTO I'm setting the MIME type '*text/x-R*' which corresponds to the file extension '*.R*'. I'm using this file type because it is a script language recognized by Gedit and it is not automatically set when the package R is installed (R is a powerful program which is a environment and a language for statistical and graphical analysis, see [http://www.r-project.org/)](http://www.r-project.org/)). In the end we will also set a customized icon to the new File/MIME type. The advantage of doing this setting is that Gedit will automatically associated the correct highlighting mode for the script language and we will have a nicer looking to the R script files.

**HOWTO**:

**1.** Create or choose a customized icon for your file type. In my case I created the icon '*gnome-mime-text-R.png*'.

[ATTACH]7627[/ATTACH]

**2.** Create a file to test the HOWTO. I created the file '*test.txt*', in the Desktop directory, with the following content:

> # short example of R script with vector manipulation and plotting

x <- c(2,3,4,5,6,9)
y <- c(7,5,4,3,2,1)
plot(x, y, pch=19)

a = 2*x - 2*y
a
plot(a)

The actual Type and MIME type of this file are '*plain text*' and '*text/plain*', respectively. The icon is the default text icon used by the current icon theme. If you open the 'test.txt' file with the Gedit program you will see that the text looks like a normal text and not a highlighted language. The same would be true for a .R file.

**3.** Create the information of the new MIME type in the file that store the the MIME types:

[FONT="Courier New"][INDENT]sudo cp /usr/share/mime/packages/freedesktop.org.xml /usr/share/mime/packages/freedesktop.org.xml_backup
sudo gedit /usr/share/mime/packages/freedesktop.org.xml[/FONT][/INDENT]

In the opened file, add the following information that contains the mime-type as '*text/x-R*' and the name of the file type (R code):

>   <mime-type type="text/x-R">
    <sub-class-of type="text/plain"/>
    <comment>R code</comment>
    <comment xml:lang="az">R kodu</comment>
    <comment xml:lang="bg">&#1050;&#1086;&#1076; &#1085;&#1072; R</comment>
    <comment xml:lang="cs">Kód R</comment>
    <comment xml:lang="cy">Côd R</comment>
    <comment xml:lang="de">R-Befehle</comment>
    <comment xml:lang="el">&#954;&#974;&#948;&#953;&#954;&#945;&#962; R</comment>
    <comment xml:lang="eo">R-kodo</comment>
    <comment xml:lang="es">Código R</comment>
    <comment xml:lang="eu">R kodea</comment>
    <comment xml:lang="fi">R-koodi</comment>
    <comment xml:lang="fr">code R</comment>
    <comment xml:lang="hu">R-kód</comment>
    <comment xml:lang="it">Codice R</comment>
    <comment xml:lang="ja">R &#12467;&#12540;&#12489;</comment>
    <comment xml:lang="ko">R &#53076;&#46300;</comment>
    <comment xml:lang="ms">Kod R</comment>
    <comment xml:lang="nb">R-kildekode</comment>
    <comment xml:lang="nl">R-code</comment>
    <comment xml:lang="nn">R-kode</comment>
    <comment xml:lang="no">R-kildekode</comment>
    <comment xml:lang="pl">Kod R</comment>
    <comment xml:lang="pt">código R</comment>
    <comment xml:lang="pt_BR">Código R</comment>
    <comment xml:lang="sq">Kod R</comment>
    <comment xml:lang="sr">R &#1082;&#1086;&#770;&#1076;</comment>
    <comment xml:lang="sv">R-kod</comment>
    <comment xml:lang="uk">&#1050;&#1086;&#1076; R</comment>
    <comment xml:lang="zh_CN">R &#20195;&#30721;</comment>
    <glob pattern="*.R"/>
  </mime-type>  

between the information of two other MIME files as in the example bellow:
> 
 [INDENT][INDENT][INDENT]...
      <glob pattern="*.py"/>[/INDENT]
   </mime-type>[/INDENT][/INDENT]
**insert here -->**
[INDENT][INDENT]  <mime-type type="text/x-readme">
    [INDENT]<sub-class-of type="text/plain"/>
    <comment>README document</comment>
    ...[/INDENT][/INDENT][/INDENT]
    
Save and close the file.

**4.** Update the MIME database with the command:

[FONT="Courier New"][INDENT]sudo update-mime-database /usr/share/mime/[/FONT][/INDENT]

and now the new file and MIME types for the *.R files will be '*R code*' and '*text/x-R*', respectively.

**4.a.** If you see a error in the parsing of the .xml file, this is because you edited wrong the freedesktop.org.xml file, so go back and adjust the file or restore the back up with the command:

[FONT="Courier New"][INDENT]sudo mv -f /usr/share/mime/packages/freedesktop.org.xml_backup /usr/share/mime/packages/freedesktop.org.xml
[/FONT][/INDENT]

and go back to step **3** of this HOWTO.

**5.** Now, let's associate the icon with the new file/MIME type. Put the icon into the directory */usr/share/icons/name_of_the_icon_theme_used/mime.types/*. Please, note that this will put the icon in a place that can be used by all users of the cumputer. **Important:** If you keep your icons in your home directory, replace */usr/share/icons* by */home/.icons/* in the next steps.

[FONT="Courier New"][INDENT]sudo mv -i path/to/file/gnome-mime-text-R.png /usr/share/icons/name_of_the_icon_theme_used/scalable/mimetypes/
[/FONT][/INDENT]

Obs: if you already has a file with this name, choose 'no' and give another name to you file. If you don't have a file with the same name you will not be asked anything.

**6.** Edit the file with the icons' information:

UPDATED Feb 10, 2007: The "mime-support" package recommends the creation of a .mime-types in the home directory instead of editing the file present in the system installation. 

[FONT="Courier New"][INDENT]sudo cp /usr/share/icons/name_of_the_icon_theme_used/mime.types /usr/share/icons/name_of_the_icon_theme_used/mime.types_backup
sudo gedit /usr/share/icons/name_of_the_icon_theme_used/mime.types[/FONT][/INDENT]

Add the following line to the mime-types file:

> text/x-R					R

Save and close the file.

To do this with other files, just replace the file and MIME type information. To associate specific programs to open your new file and MIME types follow the nautilus instructions of "open with"...

**7.** Test the files and your environment to see if everything is fine:

[FONT="Courier New"][INDENT]sudo cp path/to/file/test.txt path/to/file/test.R[/FONT][/INDENT]

Now the file test.R will appear with the customized icon. If you open this file with Gedit it will appear highlighted with the R script language.

Obs: check if your Gedit is set to show syntax highlighting by using the menu EDIT -> PREFERENCES -> SYNTAX HIGHLIGHTING and see if the box 'Enable syntax highlighting' is checked. You can also customize the highlighting colors used by Gedit...

**8.** If there is no any problem in your system or files, you can now remove the back-up files:

[FONT="Courier New"][INDENT]sudo rm /usr/share/mime/packages/freedesktop.org.xml_backup
sudo rm /usr/share/mime/globs_backup
sudo rm /usr/share/icons/name_of_the_icon_theme_used/mime.types_backup[/FONT][/INDENT]

otherwise restore them as described in **4.a**., but changing the appropriated names and paths.

and that is it.

---

### Post by iKs on 2007-01-27
Tanks a lot four your Howto :)

The only problem I have is with step 8, I dont have such a file.. :/

---

### Post by andbelo on 2007-01-27
I'm happy you liked but I gave up making these manual adjusts because every time that the system is upgraded you end up loosing your work.

For the files, it depends on the icon theme, but the mimetypes folder is usually inside a 'scalable' or 'size x size' folder, e.g. /usr/share/icons/name_of_the_icon_theme_used/128x128/mimetypes

---

### Post by iKs on 2007-01-27
> **andbelo said:**
> I'm happy you liked but I gave up making these manual adjusts because every time that the system is upgraded you end up loosing your work.

For the files, it depends on the icon theme, but the mimetypes folder is usually inside a 'scalable' or 'size x size' folder, e.g. /usr/share/icons/name_of_the_icon_theme_used/128x128/mimetypes
Well I'll see what happens at the next upgrade ;)

But I do have the flder mimetypes, I even replaced the php icon and it worked, but I dont have the file mime.types...
I'm looking at human to see if it's because I'm using Tango..

PS: Are you talking about "/etc/mime.types" ?

---

### Post by andbelo on 2007-01-29
Sorry by the confusion. Yes, the file is the "/etc/mime.types" at least in my current version: edgy. Interestingly, now it shows a comment suggesting the creation of a ".mime.type" file in the home directory. Well, good luck.

---

### Post by neocortex on 2007-01-31
This is a very usable HOWTO! Thanks a lot!
Nevertheless, I need to ask this small community of R+gedit users, have you tried to comment lines in xxx.R files. My gedit crashes everytime I try to do that. Does anoyine knows why? And a hint to fix that, maybe?

Best,
Petar M

---

### Post by andbelo on 2007-02-10
For me it works fine when I comment a line in .R files. I cannot see any reason for Gedit to crash.

---

### Post by neocortex on 2007-02-15
Yes, I managed to fix that. However, I still wonder if it is possible to slecet few lines and comment them at once?

Best,
Petar M

---

### Post by andbelo on 2007-02-15
Petar, I'm not aware of such a comment in gedit. However, a quick and dirt way of doing this is using the replace tool and replace "\n" by "\n#". The bad news is that it will replace the first occurrence under the cursor or all of them. For several lines one could press Replace untill all the desired lines are commented.

I'm currently using vim for editing R files. It works fine and has the advantage of being able to send the R commands directly to a R window (vim-r-plugin).

---

### Post by neocortex on 2007-02-17
ANDBELO, Although I am not a newbie in statistics, I am one in Linux. I have asked about the best editor, but I got so different answers and quarrels: Gvim vs Emacs. Emacs looks too much to me, and I start using vim (nice latex-suite and rest that I need), but some told me not to - bad idea. I am confused, I must admit. That is why I started using gedit as a part of gnome. Although I realized is not as powerful as vim and Emacs.

Best,
Petar

---

### Post by andbelo on 2007-02-17
I had the same issues in the past trying to find out what would be the best editor to use. :)

I noted in the forums that there is a big discussion between emacs and vim. I don't like emacs, but this is my personal preference. In my case, I'm happy with vim (I don't use Gvim). I'm sure that both have pros and cons. In the end, the program you like better and that you feel that is more productive is your best choice.

Out of curiosity: what is the problem in using vim?

Hope it helps

---

### Post by neocortex on 2007-02-20
Problem with (G)vim? Well, nothing in my opinion, but people who are experienced in Linux told me that it is not as good for my purposes as Emacs would be. And I need it for: R, python, latex, and a bit of console C\C++. More or less, that's it. In your opinion, are they those ugly Emacs-lovers who just like to make my life a misery?!? :) Would you suggest me Gvim? Or Gedit, although I am aware that it is not as powerful as other two (Gvim, Emacs).

Best,
Petar

---

### Post by andbelo on 2007-03-07
I really don't know about emac. I haven't used it. I like vim better than gedit because it offers more editing commands, so it is faster. But gedit is a good text editor too.

---

### Post by dr.koljan on 2007-08-10
I am having a problem: I did the steps you listed for docx, and now everything works fine: Ubuntu sees the mime type for docx as application/mswordx and opens these files with OpenOffice.org. However, there is a problem: there is no icon. I did edit the /etc/mime.types file adding the application/mswordx line and did make a symbolic links to /usr/share/icons/Tango/.../mimetypes/x-office-document.png(svg) and named them gnome-mime-application-mswordx.png(svg) but there is still no icon.

Please help if you can. This is really pissing me off and makes me want to switch back to Windows where it's easy to add mime types and give them icons. :(

---

### Post by andbelo on 2007-08-12
dr.loljan,

the Tango icon theme needs to have a cache updated. try this:

sudo gtk-update-icon-cache -f /usr/share/icons/Tango

---

### Post by logos34 on 2007-11-02
I want to change the default mime type icon for **.ram** (RealAudio) files in Nautilus--currently they show up as a plain text page icon.  RealVideo files appear with a framestill thumbnail like other video files, which is fine so I'll just leave it.  

Here is my /usr/share/mime/packages/freedesktop.org.xml listing for .ram:
> 
  </mime-type>
  <mime-type type="application/ram">
    <comment>RealMedia Metafile</comment>
    <glob pattern="*.ram"/>
    <sub-class-of type="text/plain"/>

There's no listing for 'application/ram' in /etc/mime.types.

I'd like to put the icon in ~/.icons (I have a separate /home) so I don't lose it next upgrade or fresh install.

So how exactly would I go about this?  Do I need to change this to 'audio/ram'?  I just don't want mess anything up.

the icon I want to use is ~/RealPlayer/share/icons/mime-application-ram_48x48.png

or, failing that, just the generic 'music note' icon that all other audio files in nautilus use

---

### Post by andbelo on 2007-11-03
Hi logos34,

rename your icon to "application-ram.png" and put it in the mimetypes folder.

Because I use Tango, I had to update the icon cache:

```
sudo gtk-update-icon-cache /usr/share/icons/Tango
```

To update the desktop view: CTRL+R

I hope it helps.

---

### Post by logos34 on 2007-11-03
THANKS Andbelo!  

Took a bit of googling to track down the correct size icon (128x128 .png) and a few tries getting it in the proper folder but it's working now.  I put it in /usr/share/icons/Human/scalable/mimetypes, but I want it in /home.  So if I create a directory ~/.icons/Human/scalable/mimetypes and move it there is that all I have to do?  Still not clear.

And what if I want to use the default Gutsy icon for sound files?  Where is it?  Mine looks almost exatly like Tangerine (I might have changed it though):

/usr/share/icons/Tangerine/scalable/mimetypes/audio-x-generic.svg

---

### Post by andbelo on 2007-11-03
Here is the trick:

You have always to match the name of the icon, which has to be inside a /icon-path/mimetypes/, with the icon file name. 

e.g. Icon "application-ram.png" for <mime-type type="application/ram">.

With this simple role you can set any icon to file type. The extension of the icons can be different (.png or .svg). They can be links in the case you want to have several file types using a single icon.

Now answering your question about the home directory, copy the entire icon folder to /home/user/.icon. Include the desirable (renamed or not) icon to mimetypes folder (it can be scalable when available for the particular theme or the correct size, i.e. 48x48, etc). If the themes are duplicated (/usr/share/icons and /home/user/.icons) the one in /home/user/.icons will have higher priority.

---

