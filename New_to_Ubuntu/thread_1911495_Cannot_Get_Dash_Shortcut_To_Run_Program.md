---
title: "Cannot Get Dash Shortcut To Run Program"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by ArtifexDominus on 2012-01-19
Hey guys, 

Let me start by saying that I am completely new to Ubuntu/Linux. I have worked through quite a bit of the learning curve the last few days but now have run into a snag and cannot find the answer for the life of me.

I am currently running Ubuntu 11.10 on a dell Inspiron 2650.

I have found some posts on permissions issues, specifically with the piece of software I am attempting to run, but that was back on version 10 and it does not seem to apply anymore. 

I have installed a program called Snowflake Pro. It is installed to "/usr/local/Snowflake Pro 1.1.1"

If I right click and run the "Snowflake.jar" with Java JRE 6 it will run, but I cannot seem to get the shortcut that comes up in the Dash's global search to run it. It simply closes the dash and nothing happens.

There is a file called "SnowPro" which is a "shell script (application/x-shellscript)". When I open this with Text Editor I get:

> #!/bin/sh
dir="${0%/*}"
cd "$dir"
exec /usr/lib/jvm/java-6-sun-1.6.0.26/jre/bin/java -cp .:lib/swing-worker-1.1.jar:lib/GData.jar:lib/mp3spi1.9.4.jar:lib/TextTools.jar:lib/iText-2.1.4.jar:lib/Utilities.jar:lib/swing-layout-1.0.4.jar:lib/tritonus_share.jar:Snowflake.jar:lib/xercesImpl.jar:lib/iText-rtf-2.1.4.jar:lib/jl1.0.1.jar:lib/appframework-1.0.3.jar com.ingermanson.snowflake.SnowflakePro "$@"I have a feeling that I am close, but I cannot find the shortcut to edit it directly, and cannot find out why nothing happens when clicking that shortcut.

I hope I have provided enough detail, if not please let me know and I would be happy to provide it. This program is one of the main reasons I have this laptop, and it was a beast to get this program installed in the first place seeing as I needed JRE 5 to run the installer :p.

---

### Post by WthIteh on 2012-01-19
The Dash is not designed to run all scripts directly. It requires some .desktop file in order to run your application.

Create a file, for example SnowflakePro.desktop, anywhere, for example on your Desktop and put these in it:
```

[Desktop Entry]
Comment=The Snowflake Pro Software
GenericName=Snowflake Pro
Name=Snowflake Pro
Icon=path to some xpm icon if you want; otherwise remove this line...
Path=/usr/local/Snowflake Pro 1.1.1
StartupNotify=true
Terminal=false
Exec=/usr/lib/jvm/java-6-sun-1.6.0.26/jre/bin/java -cp  .:lib/swing-worker-1.1.jar:lib/GData.jar:lib/mp3spi1.9.4.jar:lib/TextTools.jar:lib/iText-2.1.4.jar:lib/Utilities.jar:lib/swing-layout-1.0.4.jar:lib/tritonus_share.jar:Snowflake.jar:lib/xercesImpl.jar:lib/iText-rtf-2.1.4.jar:lib/jl1.0.1.jar:lib/appframework-1.0.3.jar com.ingermanson.snowflake.SnowflakePro

```Then make it executable with "chmod 755 SnowflakePro.desktop" and run it by clicking on it.
If it works, you could add it to unity by drag and drop, or add it to dash by placing it at "/usr/share/applications".

---

### Post by ArtifexDominus on 2012-01-19
Beautiful!

The only one thing I did not understand about this is what "xpm" means when referring to an icon. You are wonderful, thanks for the help!

File system makes a little more sense now ;)

---

### Post by WthIteh on 2012-01-19
You're welcome :) You could mark thread as Solved using links at top of page.
> **ArtifexDominus said:**
> The only one thing I did not understand about this is what "xpm" means when referring to an icon.
Desktop entry files can be configured to show an icon, but only some formats are supported. For example [PNG]("http://en.wikipedia.org/wiki/Portable_Network_Graphics") and [XPM]("http://en.wikipedia.org/wiki/X_PixMap") image formats are supported but [JPEG]("http://en.wikipedia.org/wiki/JPEG") is not supported. If you have an image in other formats you could open it with [GIMP]("http://www.gimp.org/") and convert it to another supported format.

---

### Post by ArtifexDominus on 2012-01-19
Thanks, I wanted to make sure it worked before marking solved, and I am glad I did! :) 

I think I may have made a mistake somewhere. I created the file as you said. and linked the .ico file up with the path for the icon. 

> 
[Desktop Entry]
Comment=The Snowflake Pro Software
GenericName=Snowflake Pro
Name=Snowflake Pro
Icon=/usr/local/Snowflake Pro 1.1.1/JExpress
Path=/usr/local/Snowflake Pro 1.1.1
StartupNotify=true
Terminal=false
Exec=/usr/lib/jvm/java-6-sun-1.6.0.26/jre/bin/java -cp  .:lib/swing-worker-1.1.jar:lib/GData.jar:lib/mp3spi1.9.4.jar:lib/TextTools.jar:lib/iText-2.1.4.jar:lib/Utilities.jar:lib/swing-layout-1.0.4.jar:lib/tritonus_share.jar:Snowflake.jar:lib/xercesImpl.jar:lib/iText-rtf-2.1.4.jar:lib/jl1.0.1.jar:lib/appframework-1.0.3.jar com.ingermanson.snowflake.SnowflakePro
Name[en_US]=SnowflakePro.desktopWhen I run it it says:

> "Do you want to run "SnowflakePro.desktop", or display its contents?

"SnowflakePro.desktop" is an executable text file."I then get the option to "Run in Terminal", "Display", "Cancel" or "Run".

When choosing Display, it allows me to edit the text (helpful that, couldn't figure it out at first...) and Run does not seem to do anything. I saved the file in /home/eric/SnowflakePro, as a desktop configuration file (application/x-desktop). Did I do something wrong here? I apologize for my lack of knowledge here, if you have some resources that you think may help me understand how to fix this issue myself I am very happy to learn! (not asking for a fish, im willing to learn to fish for myself ;))

Thank you again for all of your help!

---

### Post by mcduck on 2012-01-19
.desktop files don't need the execute permission. Remove that and the message about execute/open will disappear and the launcher should start working correctly.

---

### Post by ArtifexDominus on 2012-01-19
I apologize for sounding frustrated with my own lack of knowledge, but I feel that I shouldn't have to ask for this information. Linux is just very different than what I am used to. 

so the chmod 755 command changed permissions on the file as follows: 7 = Owner (read ,write, and execute) 5 = Group and Other (read, and execute)

I understand that I can add execute permissions with a chmod x command. But I am not sure how to remove that permission from a file as you suggested. Any help there? The document [here on file permissions]("https://help.ubuntu.com/community/FilePermissions") does not seem to explain how to do this. I would imagine that I would simply re-run the chmod command this time with a "chmod 666" command to changed  permissions to Read and Write (4+2 = 6) for all users (Owner, Group, and Other)?

**Edit - Doesn't the execute permission allow this to become an "executable file" rather than simply opening it for editing in textedit? I suppose I am confused as to how I am to use this as a shortcut if it is not executable?

Once again, sorry for my lack of knowledge here. I truly appreciate all the help and speedy responses!!

---

### Post by WthIteh on 2012-01-20
> **ArtifexDominus said:**
> I understand that I can add execute permissions with a chmod x command. But I am not sure how to remove that permission from a file as you suggested.
For removing executable permission you could either use
```
chmod -x file-name
```or giving new permission as
```
chmod 644 file-name
```> **ArtifexDominus said:**
> **Edit - Doesn't the execute permission allow this to become an "executable file" rather than simply opening it for editing in textedit? I suppose I am confused as to how I am to use this as a shortcut if it is not executable?
I always make .desktop files executable. Any non-executable .desktop file will not be executed by the Gnome (it's a security feature).
So I DO NOT recommend you to remove executable permission (above command was just for your knowledge).

**Solution:** I missed one item in the first posted desktop entry file which is required for executing it. Add this line to that file too:
```
Type=Application
```

---

### Post by mcduck on 2012-01-20
> **WthIteh said:**
> For removing executable permission you could either use
```
chmod -x file-name
```or giving new permission as
```
chmod 644 file-name
```
I always make .desktop files executable. Any non-executable .desktop file will not be executed by the Gnome (it's a security feature).
So I DO NOT recommend you to remove executable permission (above command was just for your knowledge).

**Solution:** I missed one item in the first posted desktop entry file which is required for executing it. Add this line to that file too:
```
Type=Application
```

The thing here is that .desktop files are not even supposed to be executed. They only contain information about the program you actually want to execute. The .desktop file itself is not a program or a script, there's no shell that would execute it. It's just a configuration file and therefore doesn't need execute permission.

Edit: and if you don't believe that, just take a look in /usr/share/applications, where the .desktop files for all the system-wide installed applications are. None of them has execute permission, yet still you are able to run your programs from the menu... ;)

---

### Post by WthIteh on 2012-01-20
> **mcduck said:**
> The thing here is that .desktop files are not even supposed to be executed.
It's not supposed to be executed like normal scripts. But **logically** it's executed. Like **folders** which are not executed of course, but require executable permission to make them possible to become current directory (for "cd" command to work).
> **mcduck said:**
> Edit: and if you don't believe that, just take a look in /usr/share/applications, where the .desktop files for all the system-wide installed applications are. None of them has execute permission, yet still you are able to run your programs from the menu... ;)
Yes, requiring executable permission is just for security.
Now copy one of those .desktop files to your Desktop. It won't run anymore!!
Here is a question about this feature <http://askubuntu.com/questions/20951/how-to-make-a-link-to-a-desktop-desktop-entry-file>

---

### Post by mcduck on 2012-01-20
> **WthIteh said:**
> It's not supposed to be executed like normal scripts. But **logically** it's executed. Like **folders** which are not executed of course, but require executable permission to make them possible to become current directory (for "cd" command to work).

Yes, requiring executable permission is just for security.
Now copy one of those .desktop files to your Desktop. It won't run anymore!!
Here is a question about this feature <http://askubuntu.com/questions/20951/how-to-make-a-link-to-a-desktop-desktop-entry-file>

No, it really *is not executed*.

It's a configuration file, you never execute the .desktop file, just like you don't need execute permission on any other of your config files.

Anyway, it's waste of time to even argue about such thing. Just try removing the execute permission from your .desktop file, and you'll see yourself.

Edit: The page you posted is about *a link to a .desktop file*. ;)

---

### Post by ArtifexDominus on 2012-01-20
> **WthIteh said:**
> 

**Solution:** I missed one item in the first posted desktop entry file which is required for executing it. Add this line to that file too:
```
Type=Application
```

And would you add this code anywhere in particular, or just in the file somewhere? Not sure if Priority matters.

Thank you both for your replies. I will try this out this morning and let you know how it goes!

---

### Post by WthIteh on 2012-01-20
> **ArtifexDominus said:**
> And would you add this code anywhere in particular, or just in the file somewhere? Not sure if Priority matters.
Order of lines has no effect. The only limit is that "[Desktop Entry]" must be the first line.

---

### Post by ArtifexDominus on 2012-01-20
Awesome! It works, one final question. I cannot seem to drag to the launcher as it classifies the .desktop as a file and will not let me. It also does not show as an icon even through I added the icon path to the file. Any thoughts?

---

### Post by WthIteh on 2012-01-20
> **ArtifexDominus said:**
> I cannot seem to drag to the launcher as it classifies the .desktop as a file and will not let me.
First run that .desktop file by clicking; it will be shown in the unity. Then right click on it in the unity and select "Keep in launcher". It will remain in unity afterwards.
**Note:** Whenever you edit .desktop file, you should remove it from unity and add it in this way again.
> **ArtifexDominus said:**
> It also does not show as an icon even through I added the icon path to the file. Any thoughts?
You used an icon with .ico format? That format is not supported. Convert it to PNG format. For this you could use GIMP or "convert file.ico file.png" command.

---

### Post by ArtifexDominus on 2012-01-20
Thanks for the advice, I was able to update the path to include the name of the PNG icon that, funny enough, comes with the install... Unfortunately I do not get a "Keep in Launcher" like normal when right clicking. Just the name, and quit. 

Thanks again for all of your help. I think I should be able to figure it out from here!

---

### Post by rijidij on 2012-03-22
Hi,

I installed Snowflake Pro yesterday and ran into this same problem.
Although the discussion about .desktop files was highly illuminating, the solution was much simpler.
Out of the box, the SnowPro script mentioned earlier doesn't have execute permission for other users (i.e. -rwxr-xr--)

Execute the following command:
```
sudo chmod 755 /usr/local/Snowflake\ Pro\ 1.1.1/SnowPro
```
..and Snowflake Pro will now run properly (with a pretty splash screen and everything ;) )
Just drag the icon from the Dashboard to the Launcher, or select Keep in Launcher if you wish.

HTH

---

