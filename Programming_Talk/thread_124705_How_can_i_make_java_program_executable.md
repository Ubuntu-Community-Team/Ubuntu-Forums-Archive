---
title: "How can i make java program executable?"
date: 2006-02-02
forum: Programming Talk
---

### Post by Packard Dell on 2006-02-02
Hi. Ok, I have created a jar file for my java program. I just only want to ask how can i make that jar file executable when it is double clicked? Or, if that can't be done with jar, is there any other method of doing it so? And also, how can i include or put that java program under *Applications > Games* menu?

Thanks....

---

### Post by drummer on 2006-02-02
You run them with the command 'java -jar file.jar', you could write a shell script to run it. Open up gedit (or your favourite text editor), and put this in it:```
#!/bin/bash
cd /path/to/javafiles
java -jar filetorun.jar
```(replacing of course the right directories/file names)

Then save the file, open a shell and cd to the directory you saved the script in. Then,```
chmod +x shellscript
sudo cp shellscript /usr/bin
```
and the program can be run like any other (ie. by typing the name of the shellscript in a terminal, in Alt-F2, or in a launcher in the menu).

To add the program to the menu, use the menu editor in Applications > System Tools.

---

### Post by Packard Dell on 2006-02-02
Thanks for your quick reply, i really appreciate it. I tried what you instructed me to do, it works if i run it from the terminal **but not** on double clicking it or by the ALT+F2 (Run Application). If you don't mind asking you this (just an additional info for me) I am wondering why do i have to copy the shell script that i created to the */usr/bin* directory?

---

### Post by drummer on 2006-02-02
Hmm... the program should work from the run application if it's in /usr/bin i think. Executable files in /usr/bin, or in /usr/local/bin, or similar can be run without having to type the full path of the executable in.

You can also run the file by typing in the full path in either a terminal or the run application and not have to put it in /usr/bin, i just think it simplifies the process (perhaps not). Perhaps try putting the script in the directory where the program is, remove the line in it with 'cd /blah/blah' and run it by entering the entire path to the script (ie. in a terminal or run application '/home/user/program/script'). Maybe i should have started off simpler, so it's easier to tell where things went wrong :P

---

### Post by darth_vector on 2006-02-02
he is putting the executable in /usr/bin to avoid changing the path variable. for self made scripts like this i would make a directory in my home directory called bin

mkdir $HOME/bin

then put the script in it and add the following to ~/.bashrc

PATH=$PATH:$HOME/bin

but its just a personal preference thing really.

---

### Post by kvorion on 2006-02-02
[QUOTE=Packard Dell] I am wondering why do i have to copy the shell script that i created to the */usr/bin* directory?[/QUOTE]

By default, all the scripts present in /usr/bin can be run directly from any location cos /usr/bin is present in ur $PATH. So if u add any script into that folder, you can run it from anywhere. 

One more thing you would have noticed is that we have to type ./progname to execute any prog in your current directory. (the ./ is for the current directory) Because of some reason they decided to not include the current directory in the path. So the best thing to do would be what darth_vector suggested. Create a folder and add it to the path variable.

---

### Post by tageiru on 2006-02-02
[QUOTE=darth_vector]he is putting the executable in /usr/bin to avoid changing the path variable. for self made scripts like this i would make a directory in my home directory called bin

mkdir $HOME/bin

then put the script in it and add the following to ~/.bashrc

PATH=$PATH:$HOME/bin

but its just a personal preference thing really.[/QUOTE]
There is no need to modify the path variable, it is already done in .bash_profile for $HOME/bin

---

### Post by darth_vector on 2006-02-02
it is too! ubuntu is full of nice things like that :)

---

### Post by drummer on 2006-02-02
Wow.. never knew that, well something new learned today.

---

### Post by Packard Dell on 2006-02-03
Thanks. I tried all your suggestions but still no luck at all. Nothing is happening when i double click it or run it from ALT+F2, but i can run it from terminal though in any directory. There must be some other way of solving this.

---

### Post by Viro on 2006-02-03
I think the reason why it only works in the Terminal, is because the files /etc/profile and $HOME/.profile (or $HOME/.bash_profile) are only read when you run the Terminal. It's a strange 'feature' (I'd call it a bug) of Debian and Ubuntu. 

Assuming you are using GNOME, try adding the PATH definitions to your JDK to the file .gnomerc in your home directory. It is the same format at .bashrc/.profile/and gang. Log out and log in again. That should make your shell script work from inside GNOME without the need for opening a terminal.

---

### Post by LordHunter317 on 2006-02-03
[QUOTE=Viro]I think the reason why it only works in the Terminal, is because the files /etc/profile and $HOME/.profile (or $HOME/.bash_profile) are only read when you run the Terminal. It's a strange 'feature' (I'd call it a bug) of Debian and Ubuntu.[/quote]No, they're not.  They ought to be persisted into the X environment, at least they are for KDM.  If GDM got broken again...

If that script is exactly as written, what does ~/.xsession-errors say when you try to run it?  What does this application do?

---

### Post by Viro on 2006-02-03
Well, they weren't for GNOME for a long time, and I remember on the Debian mailing lists about a year ago where the developers just recommended adding the definitions to .gnomerc while they sorted things out. Haven't heard of them sorting this out, and IIRC I added my definitions to /etc/profile and nothing happened, so I'm guessing things haven't changed :).

---

### Post by drummer on 2006-02-03
If you make a launcher on the panel or the desktop or whatever, there's an option to 'run in terminal'. That should allow you to still have a launcher, it'll just open up a terminal as well to run the program.

---

### Post by jerome bettis on 2006-02-03
i think the file you're looking for is /etc/gdm/gdm.conf ... have a look in there for the path, add /home/you/bin at the end and try that.

---

### Post by Cashel on 2006-02-04
System > Preferances > File Management

Under Behavior, make sure "Run executable text files when they are clicked" is selected.

Also check to make sure the file extension is the proper one for that format (I should have qouted so I'd remember if you said or not), and that its associated correctly in nautilus...

Just a guess, but hope it helps..

---

### Post by Packard Dell on 2006-02-04
[QUOTE=drummer]If you make a launcher on the panel or the desktop or whatever, there's an option to 'run in terminal'. That should allow you to still have a launcher, it'll just open up a terminal as well to run the program.[/QUOTE]

I have already tried that one mate, it opens up a terminal but disappears after one second and still no program is running.

---

### Post by Packard Dell on 2006-02-04
[QUOTE=Cashel]System > Preferances > File Management

Under Behavior, make sure "Run executable text files when they are clicked" is selected.

Also check to make sure the file extension is the proper one for that format (I should have qouted so I'd remember if you said or not), and that its associated correctly in nautilus...

Just a guess, but hope it helps..[/QUOTE]

Nothing is happening when i double clicked it.

---

### Post by Packard Dell on 2006-02-04
[QUOTE=LordHunter317]No, they're not.  They ought to be persisted into the X environment, at least they are for KDM.  If GDM got broken again...

If that script is exactly as written, what does ~/.xsession-errors say when you try to run it?  What does this application do?[/QUOTE]

Ok, this is what i have on my ~/.xsession-errors when i tried to run my simple test program "Hello World" inside the JOptionPane.showMessageDialog(). I have highlighted the part where i think errors that generated by java.

/```
etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ariel"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/MyUbuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/MyUbuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/MyUbuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/MyUbuntu:/tmp/.ICE-unix/8714

** (gnome-session:8714): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command = 
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
manager.c/2082: mount_all: mounting /dev/hdd
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_label_...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_label_
Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
mount: block device /dev/hdd is write-protected, mounting read-only
manager.c/1878: Mounted: /org/freedesktop/Hal/devices/volume_label_

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030
[COLOR="Red"][B]Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.tk() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.getPeerFromToolkit(java.lang.String, java.util.Map) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.Font(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.FontUIResource.FontUIResource(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.MetalLookAndFeel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.getUI(javax.swing.JComponent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.updateUI() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.JOptionPane(java.lang.Object, int, int, javax.swing.Icon, java.lang.Object[], java.lang.Object) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.JOptionPane(java.lang.Object, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.showMessageDialog(java.awt.Component, java.lang.Object) (/usr/lib/libgcj.so.6.0.0)
   at Hello2.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/ariel/Hello2.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more
[/B][/COLOR]
** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

```

Do you think there is something missing with the installation of my java? 
This is how i setup java on my system (this might help): 
    * I downloaded the jdk1.5.0_06 from the Sun's website.
    * Created directory for my java called ***/java*** on ***/usr*** and 
that's where i installed it.
    * Then i added **export PATH=/usr/java/jdk1.5.0_06/bin/:$PATH** to my ~/.bashrc to set its classpath.

Cheers mate...

---

### Post by Packard Dell on 2006-02-04
[QUOTE=Viro]I think the reason why it only works in the Terminal, is because the files /etc/profile and $HOME/.profile (or $HOME/.bash_profile) are only read when you run the Terminal. It's a strange 'feature' (I'd call it a bug) of Debian and Ubuntu. 

Assuming you are using GNOME, try adding the PATH definitions to your JDK to the file .gnomerc in your home directory. It is the same format at .bashrc/.profile/and gang. Log out and log in again. That should make your shell script work from inside GNOME without the need for opening a terminal.[/QUOTE]

Couldn't find **.gnomerc** in my home directory. Thanks.

---

### Post by Viro on 2006-02-04
You need to create the file .gnomerc in your home directory if it doesn't exist.

---

### Post by Packard Dell on 2006-02-04
[QUOTE=Viro]You need to create the file .gnomerc in your home directory if it doesn't exist.[/QUOTE]

Well done mate! You are a genius! This now solved my problem! Many thanks to you and for all the replies!

One more thing if you don't mind, just for curiosity sake, i had this error messages from my ~/.xsession-errors:

```
etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ariel"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/MyUbuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/MyUbuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/MyUbuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/MyUbuntu:/tmp/.ICE-unix/8714

** (gnome-session:8714): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command = 
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
manager.c/2082: mount_all: mounting /dev/hdd
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_label_...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_label_
Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
mount: block device /dev/hdd is write-protected, mounting read-only
manager.c/1878: Mounted: /org/freedesktop/Hal/devices/volume_label_

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.tk() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.getPeerFromToolkit(java.lang.String, java.util.Map) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.Font(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.FontUIResource.FontUIResource(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.MetalLookAndFeel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.getUI(javax.swing.JComponent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.updateUI() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.JOptionPane(java.lang.Object, int, int, javax.swing.Icon, java.lang.Object[], java.lang.Object) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.JOptionPane(java.lang.Object, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JOptionPane.showMessageDialog(java.awt.Component, java.lang.Object) (/usr/lib/libgcj.so.6.0.0)
   at Hello2.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/ariel/Hello2.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8831): WARNING **: IPP request failed with status 1030
```

What are those? Because there are some failures and warnings, should i worry about them? And the java error seems like it is looking for the /usr/lib/libgcj.so.6.0.0?

---

### Post by Viro on 2006-02-04
Well, the problem is that files like .bash_rc and .profile aren't read when you log in to GNOME. They are only read when you launch a terminal. That is why you can run your script correctly when you launch it from the terminal (as the PATH is set correctly). However, when you try running it outside the terminal, the path still isn't set (I think this is a bug of GNOME, but apparently it's a feature :-/), so you get all those errors as you are using GCJ and not Sun's JVM to run that application. Setting your definitions in .gnomerc solves it.

In my book, this qualifies as a hack and really should be fixed. But hey, as long as a workaround works, I'm happy :).

---

### Post by aamukahvi on 2006-03-27
[QUOTE=kvorion]One more thing you would have noticed is that we have to type ./progname to execute any prog in your current directory. (the ./ is for the current directory) Because of some reason they decided to not include the current directory in the path.[/QUOTE]
1) Someone makes a .tar.gz available for download.
2) this package contains (among many other files) an executable called, for example "cat"
3) ./ is in the path
4) user extracts this package and tries to "cat README"
5) the malicious script called "cat" in the present working directory is executed

Something along those lines... :-k

---

