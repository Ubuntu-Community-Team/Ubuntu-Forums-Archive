---
title: "HOWTO: Adjust screensaver settings in Dapper"
date: 2006-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by 23meg on 2006-06-17
*(Update - 17.12.06: This guide works in Edgy as well.)*

As you're probably aware, the gnome-screensaver GUI that ships with Dapper's GNOME 2.14.1 doesn't give the user any control on individual screensaver settings. I had previously posted [a guide on replacing gnome-screensaver with xscreensaver]("http://ubuntuforums.org/showthread.php?t=195557"), but it has a few drawbacks (which I listed in the linked thread) that some users may find deterrent. Hence the reason for this guide, which does the job in a more elegant but maybe slightly less convenient way.

This will show you how to set preferences for your screensaver by figuring out the required command line with xscreensaver and putting it manually in the screensaver's gnome-screensaver theme file. It takes a bit more manual work, but **I prefer this method over the other one** since it doesn't have the drawbacks of replacing gnome-screensaver altogether, and it's more "technically correct". 

To compare, the other method is a bit more convenient if you adjust settings very often, but this one doesn't break anything and doesn't touch the Ubuntu defaults. It's up to you to decide which one to use.

[SIZE="3"]**1.**[/SIZE] Install xscreensaver. ```
sudo apt-get install xscreensaver
```Note that unlike the other method, you won't actually be running xscreensaver full time; you'll only need its preferences interface to adjust screensaver settings to your liking and preview them.

[SIZE="3"]**2.**[/SIZE] When you want to adjust the settings of a particular screensaver, launch the xscreensaver preferences dialog with ```
xscreensaver-demo
```and when asked whether you want to launch the daemon, **[SIZE="4"]click "Cancel"[/SIZE]. This is important, since running both the xscreensaver and gnome-screensaver daemons together is very likely to cause unwanted behavior.**

Choose the screensaver you want, click "Settings" to adjust its settings, and click "OK" to go back. In the Advanced" tab of the main window adjust image and text manipulation settings as you like. Check the preview area to see if it works the way you want, or hit "Preview" for a full screen preview. Once it's working as you want, click "Settings" and then "Advanced", and copy the string in the "Command Line" string box.

[SIZE="3"]**3.**[/SIZE] Open the gnome-screensaver theme file that corresponds to your selected screensaver in /usr/share/gnome-screensaver/themes (in edgy this is /usr/share/applications/screensavers). For the Phosphor screensaver you'd have to do ```
gksudo gedit /usr/share/gnome-screensaver/themes/Phosphor
```Locate the line that begins with **"Exec="** and replace the command that follows it with the command you copied from xscreensaver's "Command Line" box.

[SIZE="3"]**4.**[/SIZE] Open the gnome-screensaver preferences window (System / Preferences / Screensaver) and choose your preferred screensaver there.

[SIZE="3"]**5.**[/SIZE] Hit Alt+F2 and enter ```
gnome-screensaver-command --lock
```to test if the screensaver is behaving as you like.

[SIZE="3"]**6.**[/SIZE] [COLOR="Gray"]Optional:[/COLOR] Install the extra screensavers in the repositories that don't come installed as default. ```
sudo apt-get install xscreensaver-data-extra xscreensaver-gl-extra
```

For convenience you may want to use Alacarte or tweak the files in /usr/share/applications to create a separate Applications menu entry for xscreensaver called "Screensaver Settings" and rename the existing "Screensaver" item to "Screensaver Selection".

---

### Post by n00bWillingToLearn on 2006-06-26
Thank you 23 meg, I knew there must be a better way to do this. If I have some extra time I might make a bash script to "update" the gnome-screensaver config files to after running xscreensaver-demo. Basically, my idea would be to make the script open xscreensaver-demo, then, after xscreensaver exits, grep it's config files for "Exec=" and replace the line found in the xscreensaver config file, with the corrosponding one in the gnom-screensaver config file. The reason why I would have the script open xscreensaver-demo itself is so it could be added using alecarte as a menu item and violla: You click on the screensaver preference menue item as you normally would, edit the preferences in xscreensaver, and yet still be able to use gnome-screensaver. It would be completely transparent to the user if it weren't for the promt asking you to launch the demon.


Note: I have NEVER made a bash script before, and although I have done some programming before, I am new to linux. I also may not have the time to make this script so if anyone is interested in making a script to do this, I don't see why it should be very hard for someone with more expierience, PLEASE don't wait for me to do it as I may never get to it. That is why I am posting this so that if I never get the ball rolling someone else can take off with it.

---

### Post by 23meg on 2006-06-27
Thanks for the input; while testing some of the more obscure screensavers with this method today I was thinking of something along those lines; not the exact methodology though. I'll get to it and see what I can do as soon as I get some free time.

---

### Post by n00bWillingToLearn on 2006-07-01
I have almost finished my program so I thought I would post what I have since I don't know when I'll get back to it.

As far as I can tell all that I have to do to make this work is to change the changeCommand method to work even if TrExec= ( the command used to preview a screensaver ) comes before Exec= as it is searching for Exec= which is in TrExec=. I would fix the problem now but it is late and bad things happen when I try to program tired. So here it is ( in java ) for anyone that is curious or would like to make any suggestions ( just please don't run it, I am not posting the .class file because this is unfinished and needs to run as root, so if it breaks it could be very bad and I take no responsability ) that being said, to run it run ```
sudo java ConfigSaver ~/.screensaver
``` 

```
import java.io.*;
public class ConfigSaver{
    public static String pathToGnomeThemes = "/usr/share/gnome-screensaver/themes/";
    public static void main(String[] args){
        String xscreensaver = readFile(args[0]);
        // finds the names of all the screensavers by looking at thier .desktop filenames
        String[] screenSavers = getFileNames(pathToGnomeThemes);
        // strips the .desktop from the filename ( leaving only the name of the screensaver )
        for(int i=0; i< screenSavers.length; i++){
            String temp = screenSavers[i];
            temp = temp.substring(0, temp.length()-8);
            screenSavers[i] = temp;
        }
        // edits the .desktop files to update the command
        for(int i=0; i< screenSavers.length; i++){
            String saverName = screenSavers[i];
            String command = getCommand(xscreensaver, saverName);
            if(command != null){
                String saverConfig = readFile(pathToGnomeThemes + saverName + ".desktop");
                String newSaverConfig = changeCommand(saverConfig,command);
                writeFile(pathToGnomeThemes + saverName + ".desktop", newSaverConfig);
            }
        }
    }

    public static String readFile(String filePath){     
        try { 
            BufferedReader input = new BufferedReader(new InputStreamReader(new FileInputStream(filePath))); 
            String text=input.readLine();
            String line = input.readLine(); 
            while(line !=null){
                text+= "\n"; 
                text+=line;
                line = input.readLine(); 
            } 
            return text; 
        } 
        catch(IOException e) { 
            e.printStackTrace(); 
            return null; 
        } 
    }

    public static boolean writeFile(String filePath,String text){    // returns true if successfull, false if write failed.
        try{ 
            String toOut = text; 
            PrintStream output = new PrintStream(new FileOutputStream(filePath)); 
            output.print(toOut); 
            output.close(); 
        }
        catch(IOException e){
            e.printStackTrace();
            return false;
        }
        return true;
    }
    
    public static String[] getFileNames(String directory){ 
        return new File(directory + ".").list(); 
    }
    
    public static String getCommand( String xscreensaver, String saverName){
        int startOfCommand = xscreensaver.indexOf(saverName);
        if(startOfCommand == -1){
            try{
                return null;//return javax.swing.JOptionPane.showInputDialog(saverName + " doesn't seem to have a corrosponding xscreensaver, enter the command you would like gnome-screensaver to use then hit OK \n or hit cancel to not change the command");
            }
            catch(Exception e){ // I only expect an exception to be thrown if this is being run on the open source JVM that does not implement most of swing
                System.out.println(saverName + " was not modified because there doesn't seem to be a corrosponding xscreensaver ( this is normal and nothing to worry about )");
                return null;
            }
        }
        String temp = xscreensaver.substring(startOfCommand);
        int endOfCommand = temp.indexOf("\\n\\");
        String command = temp.substring(0,endOfCommand);
        // remove any hard returns from the command
        while( command.indexOf("\n") != -1 ){
            temp = command.substring(0,command.indexOf("\n"));
            command = temp + command.substring(command.indexOf("\n")+1);
        }
        // remove any \s from the command
        while( command.indexOf("\\") != -1 ){
            temp = command.substring(0,command.indexOf("\\"));
            command = temp + command.substring(command.indexOf("\\")+1);
        }
        // remove any tabs from the command
        while( command.indexOf("    ") != -1 ){
            temp = command.substring(0,command.indexOf("    "));
            command = temp + command.substring(command.indexOf("    ")+1);
        }
        // remove any consecutive spaces (removes only one space so, for instance "-option  1" would become "-option 1" and "-option       1" would also become "-option 1"
        while( command.indexOf("  ") != -1 ){
            temp = command.substring(0,command.indexOf("  "));
            command = temp + command.substring(command.indexOf("  ")+1);
        }
        return command;
    }
    
    public static String changeCommand(String saverConfig, String command){
        if(saverConfig.indexOf("Exec=")< saverConfig.indexOf("TryExec")){
            String configBeforeCommand = saverConfig.substring(0,saverConfig.indexOf("Exec=") -1);
            String temp = saverConfig.substring(saverConfig.indexOf("Exec="));
            String configAfterCommand = temp.substring(temp.indexOf("\n"));
            saverConfig = configBeforeCommand + "Exec=" + command + configAfterCommand;
        }
        else{
            int startIndexOfCommand = saverConfig.indexOf("TryExec=") + 8;
            String temp = saverConfig.substring(startIndexOfCommand);
            startIndexOfCommand += temp.indexOf("Exec="); //-1;
            temp = saverConfig.substring(startIndexOfCommand);
            String configBeforeCommand = saverConfig.substring(0,startIndexOfCommand);
            String configAfterCommand = temp.substring(temp.indexOf("\n"));
            saverConfig = configBeforeCommand + "Exec=" + command + configAfterCommand;
        }     
        return saverConfig;
    }
}
```

[edit] updated code to working version

---

### Post by n00bWillingToLearn on 2006-07-01
My program is now working perfectly ( as far as I can tell ) so if anyone has an installation they are willing to lose ( I don't see any way that my program could do anything other than screw up you screensavers but anything is possible and nobody other than me has tried it yet or looked at the code for possible bugs so don't run this on your main installation ) for instance on a liveCD or a spare computer / partition here are the steps to set this up:

[SIZE=3]**1.**[/SIZE] Install xscreensaver. ```
sudo apt-get install xscreensaver  
``` [SIZE=3]**2.**[/SIZE] Download my program and the shell script to run it ```
wget [http://trogdoor.googlepages.com/ConfigSaver.class]("http://trogdoor.googlepages.com/ConfigSaver.class")
wget [http://trogdoor.googlepages.com/ConfigSaver]("http://trogdoor.googlepages.com/ConfigSaver.class")
``` [SIZE=3]**3.**[/SIZE] make the script executeable: ```
 chmod +x ~/ConfigSaver 
``` [SIZE=3]**4. **[/SIZE]You should now have two new files in your home folder, 'Configsaver.class' and 'ConfigSaver'. ConfigSaver is the script that will run my program, all you need to do is double click it. You can move ConfigSaver anywhere you want but ConfigSaver.class should stay in your home folder. When you double click on ConfigSaver the xscreensaver preferences should open up and you can change the settings of the screensavers, when you close the xscreensaver window, a dialog should come up asking you for your password ( I am trying to find a way around this but I would like a confermation that the program works as is before I work on that) enter your password and hit OK and your preferences should now be updated in gnome-screensaver**.**

---

### Post by mgmiller on 2006-07-02
Great piece of work.  

Before I try installing this on a spare dapper machine, I was wondering where to put the file that I download from you.  From the alacarte command, you seem to imply that it would go in my home directory in a directory named ConfigSaver.  Is this correct?  The path would look like this on my machine:   /home/marty/ConfigSaver/ConfigSaver.class

It's folks like you that help make this the best Linux distro out there.

---

### Post by 23meg on 2006-07-02
[QUOTE=n00bWillingToLearn]My program is now working perfectly [/quote]Thanks a lot for the effort, but it doesn't work here; the preferences I set with xscreensaver don't apply to gnome-screensaver. I'm investigating the reason; maybe it's due to my tweaked configuration. 

Also having to grant root privilege to the app isn't very elegant but I guess since it has to write to /usr there's no way around that, right?

---

### Post by n00bWillingToLearn on 2006-07-02
[quote=23meg]Thanks a lot for the effort, but it doesn't work here; the preferences I set with xscreensaver don't apply to gnome-screensaver. I'm investigating the reason; maybe it's due to my tweaked configuration. 

Also having to grant root privilege to the app isn't very elegant but I guess since it has to write to /usr there's no way around that, right?[/quote] 
I shouldn't have said perfectly because I havn't had anyone else test it or look at the code but it works for me. The command I gave doesn't work in Alacarte for me for some reason ( I was hoping that was a problem on my machine with Alacarte, either it's not, or my program really doesn't work ). Try entering the command directly into the terminal or try using this shell script [http://trogdoor.googlepages.com/ConfigSaver]("http://trogdoor.googlepages.com/ConfigSaver") ( you will have to change the permissions to make it executable ). As for the running as root, I agree completely and don't like it much either. It may be possible to just change the privaleges of the themes folder although I don't know if that would break anything else.

Please try again entering the command into the terminal and, to be clear, the reason this should be run on a scratch computer is because, as root, it could break your entire system ( or give me complete controll over it without your knowlage ). 

If anyone could give input on wether or not it would be safe to change the permissions of the themes folder that would be great.

If anyone could look over the code itself that would be wonderfull.

---

### Post by n00bWillingToLearn on 2006-07-04
[quote=mgmiller]Great piece of work.  

Before I try installing this on a spare dapper machine, I was wondering where to put the file that I download from you.  From the alacarte command, you seem to imply that it would go in my home directory in a directory named ConfigSaver.  Is this correct?  The path would look like this on my machine:   /home/marty/ConfigSaver/ConfigSaver.class

It's folks like you that help make this the best Linux distro out there.[/quote]

ConfigSaver.class should go directly in your home folder and for some reason ( probably my fault ) the command I gave doesn't work in Alacarte so I have updated my instructions to use a simple bash script ( basically the same command except in a bash script instead of in Alacarte ) and to clarify things a little more.

---

### Post by lost.sync on 2006-08-09
thanks to both of you for the HowTo and the app but i'm still left wondering...why aren't these settings just availible from within the gnome-screensaver dialog?  'few options, sane defaults,' okay i get it but i mean...c'mon...

---

### Post by 23meg on 2006-08-09
> **lost.sync said:**
> thanks to both of you for the HowTo and the app but i'm still left wondering...why aren't these settings just availible from within the gnome-screensaver dialog?  'few options, sane defaults,' okay i get it but i mean...c'mon...

[http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions](http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions)
[http://www.ubuntuforums.org/showpost.php?p=1314185&postcount=17](http://www.ubuntuforums.org/showpost.php?p=1314185&postcount=17)
[http://bugzilla.gnome.org/show_bug.cgi?id=316654](http://bugzilla.gnome.org/show_bug.cgi?id=316654)
[https://launchpad.net/distros/ubuntu/+source/gnome-screensaver/+bug/22007](https://launchpad.net/distros/ubuntu/+source/gnome-screensaver/+bug/22007)

---

### Post by bones78 on 2006-08-29
It might be me but for some reason when I try to open the file in themes with gedit, all I get is a blank gedit file.  What am I doing wrong?

---

### Post by khedron on 2006-08-31
How would I change settings that are global to all screensavers, like where to pull pictures from?

---

### Post by city-17 on 2006-10-02
Your guide is great!. Thanks for posting it, worked fine for me.

---

### Post by airtonix on 2006-10-21
hey guys, i was looking in the /usr/share/gnome-screensaver directory and i found that there was a glade project file sitting there....

```

~$ ls /usr/share/gnome-screensaver
gnome-screensaver-preferences.glade  themes

```

any ideas  as to its purpose?

---

### Post by Bil-E-daKid on 2006-10-26
> How would I change settings that are global to all screensavers, like where to pull pictures from?

Hey there - did you ever figure out that one?

---

### Post by khedron on 2006-10-27
> **Bil-E-daKid said:**
> Hey there - did you ever figure out that one?

Nope, afraid not. I didn't get too much time to try though, as I 'upgraded' to kubuntu a short time afterwards. So it might still be in there somewhere.

---

### Post by thoughts on 2006-11-02
I believe the "Pictures Folder" screensaver pulls images from /home/username/Pictures and the "GLSlideshow" screensaver pulls images from /usr/share/backgrounds but this may depend on your version of Ubuntu and/or the screensaver package.  I'm running Edgy on 3 different systems now and the screensaver situation is buggy.  For example on one of these systems, both of the image screensavers I just mentioned work fine in the screensaver preview, but they don't display any images (just a blank screen) when the screensaver actually kicks in after the system becomes idle.  On another system they seem to work OK sometimes, but other times they just display a blank screen like the first system does.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by Bil-E-daKid on 2006-11-02
Oh - oh!!  I figured it out all by myself.

On my edgy machine at work (where GLSlideshow works fine), I have the following line in a '.xscreensaver' file in my home folder:

imageDirectory: /home/wgordon/media/wallpapers/screensavers

On my edgy machine at home (where GLSlideshow just plays some standard backgrounds), there was no .xscreensaver file.

I SSH'd my work one home, modified that line to point to where the images are at home and then logged in to home remotely (using FreeNX) to test it - now it works fine at home as well.

So there you go, gnome-screensaver/GLSlideshow still looks at the .xscreensaver file for some configuration options.

Wooohooo!  :D

---

### Post by hazza96 on 2006-11-11
> **airtonix said:**
> hey guys, i was looking in the /usr/share/gnome-screensaver directory and i found that there was a glade project file sitting there....

```

~$ ls /usr/share/gnome-screensaver
gnome-screensaver-preferences.glade  themes

```

any ideas  as to its purpose?
The suggested "fix" does not on Edgy because of this issue!! The directory you should be looking at is **/usr/share/applications/screensaver**

Now to find out how to copy and modify the glslideshow.desktop file so that I can create several screensavers that use different directorys as the source.

---

### Post by Campitor on 2006-11-22
Hi.  

 Hope this thread is still alive.  I don't care much about settings, I just want to disable a bunch of savers that are very hardware demanding, and some that are just plain ugly.  How can I easily do this?? I've tried to find a conf.file that will allow me just to comment out the savers I don't want.  Maybe I've been looking in the wrong places...I'm not too savy when it comes to modifying files, so please don't ommitt the obvious.

thanks in advance

---

### Post by Bil-E-daKid on 2006-11-22
Hey there,

From what I can tell, the list of available screensavers directly relates to files in the /usr/lib/xscreensaver location.

As a test, I moved out all the files starting with m and then started the screensaver panel and, lo, all the screensavers starting with m had disappeared.

It looks like you just need to remove the files for the screensavers that you want to go away.  Perhaps move them to another location just in case you want them back at some point....

:-)

---

### Post by Cariboo1938 on 2006-12-16
Hi all,
I hope this thread is still alive, because I want to know if I can apply the instructions (HOWTO: Adjust screensaver settings in Dapper) for for Edgy too?

---

### Post by 23meg on 2006-12-17
Yes it does; the only difference is that the screensaver themes are stored in /usr/share/applications/screensavers .

---

### Post by Cariboo1938 on 2006-12-20
> **23meg said:**
> Yes it does; the only difference is that the screensaver themes are stored in /usr/share/applications/screensavers .Hello 23meg,
I was away for a few days and found this today...I think it's the answer two my question. Thanks a lot...I try tonight!
Cariboo

---

### Post by dief-eh? on 2006-12-21
> **23meg said:**
> *(Update - 17.12.06: This guide works in Edgy as well.)*

As you're probably aware, the gnome-screensaver GUI that ships with Dapper's GNOME 2.14.1 doesn't give the user any control on individual screensaver settings. I had previously posted [a guide on replacing gnome-screensaver with xscreensaver]("http://ubuntuforums.org/showthread.php?t=195557"), 
<snip>


Hello,

Thank you for both your how-to guides. I'm afraid I'm still a bit confused. I've got Edgy working great, and the screensaver cycling through a stripped-down Pictures folder, but occasionally, I'd really like to be able to use Melchior Franz' excellent clock screensaver, which exists in /usr/share/applnk/System/Screensavers. 

Can I just copy/move that file into /usr/share/applications/ screensavers? 

Could it really be that simple? Or will I break something? :c)

---

### Post by carney1979 on 2007-01-15
> **hazza96 said:**
> The suggested "fix" does not on Edgy because of this issue!! The directory you should be looking at is **/usr/share/applications/screensaver**

Now to find out how to copy and modify the glslideshow.desktop file so that I can create several screensavers that use different directorys as the source.

I only wanted to modify Euphoria on my Edgy machine, so I first opened a terminal and typed:

```
man euphoria
```I was able to determine the switches I needed to make Euphoria run as I liked so I then opened the Euphoria file with:

```
sudo gedit /usr/share/applications/screensavers/Euphoria
```After using 'man euphoria' I knew that changing the following line:

```
Exec=euphoria -r
```to:

```
Exec=euphoria -r -p 1
```..would give me the desired results.

Hope this example helps my fellow Edgy users out there.

David

---

### Post by Cariboo1938 on 2007-01-30
Hi,
I'm still struggling with meg23's [HOWTO.]("http://www.ubuntuforums.org/showthread.php?t=198809")

Here is what I do:
> 1. Install xscreensaver.
Code:
sudo apt-get install xscreensaver

[COLOR="Magenta"]**After this two new packages were installed: xscreensaver and xscreensaver-data!**[/COLOR]


> 2. When you want to adjust the settings of a particular screensaver, launch the xscreensaver preferences dialog with
Code:
xscreensaver-demo
and when asked whether you want to launch the daemon, click "Cancel".

**[COLOR="Magenta"]After this command the preview window opens but I never was asked if I want to launch the daemon![/COLOR]**


> 3. Open the gnome-screensaver theme file that corresponds to your selected screensaver in
/usr/share/applications/screensavers. For the Phosphor screensaver you'd have to do
Code:
sudo gedit /usr/share/gnome-screensaver/themes/Phosphor

[COLOR="Magenta"][B]On my system there is no such directory as /usr/share/gnome-screensaver/themes/!
[/B][/COLOR]

Here I gave up because I can't figure out what went wrong! 
Can somebody help, please!

---

### Post by khedron on 2007-01-31
Are the files in 
/usr/share/applications/screensavers/
instead? There was a change with Edgy.

---

### Post by Cariboo1938 on 2007-01-31
> **khedron said:**
> Are the files in 
/usr/share/applications/screensavers/
instead? There was a change with Edgy.
Yes, the files are in /usr/share/applications/screensavers.
In /usr/share/gnome-screensaver are only the text files "gnome-screensaver-preferences.glade" and 'lock-dialog-default.glade". Do I have to transfer the files to this /usr/share/gnome-screensaver/themes/  location?

---

### Post by Cariboo1938 on 2007-01-31
> **khedron said:**
> Are the files in 
/usr/share/applications/screensavers/
instead? There was a change with Edgy.
Yes, the files are in /usr/share/applications/screensavers.
In /usr/share/gnome-screensaver are only the text files "gnome-screensaver-preferences.glade" and 'lock-dialog-default.glade". Do I have to transfer the files to this /usr/share/gnome-screensaver/themes/  location?

---

### Post by Cariboo1938 on 2007-02-01
](*,) Bump! Got stuck! Help?

---

### Post by MyR on 2007-04-29
is any of this possible in feisty fawn? i can't find the necessary configuration files

EDIT: i figured it out. see below

---

### Post by MyR on 2007-04-29
**how to adjust/configure screensaver settings in ubuntu 7.04 feisty fawn**

follow steps 1 and 2 in the tut for dapper

3. open nautilus as root and find the screensaver directory
```
sudo nautilus
```

/usr/share/applications/screensavers

4. right click on the screensaver you want to configure. click properties and go to the launcher tab. paste or type your command into the box labeled command. then close.

continue with steps 5 and 6

---

### Post by cheezwiz789 on 2007-05-24
So, to make the script work in Feisty, could I just change the "pathToGnomeThemes" string?

---

### Post by MyR on 2007-05-24
> **cheezwiz789 said:**
> So, to make the script work in Feisty, could I just change the "pathToGnomeThemes" string?

As far as I know, feisty does not have the necessary files for the script to work. however, my updated feisty tutorial above (post #34) works for sure.

---

### Post by graigsmith on 2007-07-22
i wish they would just go back to the old screensaver thing. this new gnome screensaver that you cant configure just sucks. and you guys took away all the cool 2d screensavers. why?

---

### Post by punong_bisyonaryo on 2007-08-11
> **23meg said:**
> [https://launchpad.net/distros/ubuntu/+source/gnome-screensaver/+bug/22007](https://launchpad.net/distros/ubuntu/+source/gnome-screensaver/+bug/22007)

There were several people who mentioned in the above bug thread that they were willing to give money to someone who could program a fix. 

Where can we find such people?

As far as I know, to get something changed, you either have to know how to code, convince someone to do it for you, write a technical proposal or something, or have widespread clamor for such and such feature (which still has no guarantee developers will listen).

I have tried your solution, and it fits perfectly for my needs. However, many people who are trying Linux for the first time will play around with the simple stuff, like screensavers, colors, backgrounds, etc. So I think the ability to play around with the screensavers is standard-issue, if not useful.

---

### Post by Liet_Kynes on 2008-02-04
Has this been fixed in Gutsy/Hardy?

This is a long way of setting up a screensaver

---

### Post by punong_bisyonaryo on 2008-02-04
> **Liet_Kynes said:**
> Has this been fixed in Gutsy/Hardy?

This is a long way of setting up a screensaver

Yes it is. I am still waiting for a fix (Yes, GNOME, it's a fix:mad:).

As of Gutsy, the sad truth remains.

---

### Post by piercleo on 2008-07-03
Ty for this howto, only problem is that xscreensaver does not have an f-spot screensaver and I wanted to use your solution to slow cown the transition of my f-spot screensaver. Any idea on the question ?

Best best
PC

ps: i don't like the slideshow option.

---

### Post by helpdeskdan on 2008-09-18
Screensaver Settings.  Works great!

[http://software.xfx.net/utilities/sss/download.htm](http://software.xfx.net/utilities/sss/download.htm)

---

### Post by Subban on 2008-10-08
Has anyone got a solution to edit screen saver configs? Where is the configuration for the screensavers kept, without reverting to xscreensavers, I'll edit it by hand no problem if I knew where they were.

Its insane that this is *still* a problem after what, 18 months ?

I tried the screensaver-settings suggested in the post above, and it mostly works, its hanging on exit sometimes and it is allowing me to set and configure screensavers that won't run (just results in a blank screen when it kicks in, I'm looking at popsquares here). I am guessing gnome-screensaver is detecting xscreensaver ones which gnome-sceensaver doesn't want to run even if they are put in /usr/share/applications/screensavers with the others.

Seriously, the guy upstream who refuses to see this as a problem wants powerspanking. Linux prides itself on its ability to be tweaked and configured, one of the first things my brother tried to do when I moved my mothers PC over to Ubuntu was change his wallpaper and screensaver. Well you can imagine the scene when he finds he can't even change the GLText or other settings in the screensavers, he was then quite rightly berating Linux and asking why they were using it instead of Windows, its somewhat hard to defend such a bonkers limitation as not being able to adjust a screensaver config because one person feels its been done wrong for the last 20years, and hasn't actually produced a method that your average desktop user can use to do it. Ubuntu is primarily aimed at home users isn't it? 

Sorry for rant, it annoyed me when it happened in Dapper, and I had pretty much ignored it since and was pretty much mortified to realise its *still* like it.

---

### Post by MyR on 2008-10-08
> **MyR said:**
> **how to adjust/configure screensaver settings in ubuntu 7.04 feisty fawn**

follow steps 1 and 2 in the tut for dapper

3. open nautilus as root and find the screensaver directory
```
sudo nautilus
```

/usr/share/applications/screensavers

4. right click on the screensaver you want to configure. click properties and go to the launcher tab. paste or type your command into the box labeled command. then close.

continue with steps 5 and 6

my guide should still work for hardy. this solution does NOT use xscreensaver for anything other than figuring out the proper command to paste in step 4.

peace

---

### Post by bl1rt on 2008-12-05
> Seriously, the guy upstream who refuses to see this as a problem wants powerspanking. 

Hihi, very well put, Subban. As far as I know, those GNOME guys want as few configuration stuff as possible to not overwhelm the user, but that spirit seems to have become obsessive.
On the other hand, a lot of problems concerning GNOME appear to have been lacked attention lately. I suppose all the new graphical mumbo jumbo with compiz and stuff binds a lot of resources.
It's a shame though cause it makes my favorite environment much less appealing. I even think about changing to KDE or some other window manager though I like GNOME best for being most elegant, but that argument only counts to a certain extend.

---

### Post by punong_bisyonaryo on 2008-12-06
I have two screensaver configs in my preferences menu!

I'm not sure if it was because of a recent update, or because I installed the Eternity screensaver. One is the default, where you can only pick one screensaver, and the other one where there is a checkbox for each screensaver you wanna activate.

Can anyone confirm if this was caused by installing the Eternity screensaver? Also, would there be a way to remove one of them?

---

### Post by warpasylum on 2009-05-04
Hey guys,
     Trying to update the paths for the pictures that the Ripples screensaver uses. I removed the pictures that I don't want used from /usr/share/backgrounds which is where it grabs them from. Now when i run the screensaver it still looks for the files i removed and shows them as a broken link, i.e. flaming t.v. and color bars pic. Any ideas on how to fix? Thanks. By the way, I'm still using Gnome screensaver.

---

### Post by MyR on 2009-05-04
> **warpasylum said:**
> Hey guys,
     Trying to update the paths for the pictures that the Ripples screensaver uses. I removed the pictures that I don't want used from /usr/share/backgrounds which is where it grabs them from. Now when i run the screensaver it still looks for the files i removed and shows them as a broken link, i.e. flaming t.v. and color bars pic. Any ideas on how to fix? Thanks. By the way, I'm still using Gnome screensaver.

I can't find anywhere in the config file to change the folder.

They're all in /usr/share/xscreensaver/config/
you can make a backup, open it up with a text editor (as root), and play around or search the web.

good luck!
peace

---

### Post by warpasylum on 2009-05-04
Thanks man. I'm backing up now then i'll try playing with the config. been searching the web all day n' no luck. i'll post back with any changes.

---

### Post by warpasylum on 2009-05-04
no luck man. looks like i'm gonna have to find other pics that i do like n' give them the same names as the old ones. then at least it'll show the pics that i want.

---

### Post by MyR on 2009-05-04
> **warpasylum said:**
> no luck man. looks like i'm gonna have to find other pics that i do like n' give them the same names as the old ones. then at least it'll show the pics that i want.

Yea they're probably hard-coded into the screensaver.  There's nothing about the folder in the ripples manual either.

---

### Post by warpasylum on 2009-05-04
s'all good. taking the pics i like n' naming the same as the ones i removed gets it done. Thanks for the help.

---

### Post by Subban on 2009-05-05
At the danger of repeating myself, as much as I love and support Linux and Ubuntu, I am appalled that the screensaver settings *problem* is still an issue.

I have helped another 3 people who didn't have a specific reason for using Windows to convert to Ubuntu and each person one way or another has commented on, or thought that their install was broken due to not being able to find/adjust a way to configure the settings.

It does not simplify the screensaver by removing its configuration, it just makes people look for something they expect to be there, and isn't. When each of these people has asked me about it, I have no logical argument for it not being adjustable and as new users they are then immediately antagonised in my opinion against Linux.

Its just so damned illogical removing it. Yes it still bugs me after all this time that I can't adjust colours, folder locations or graphics complexity settings of them and I'm sure I am not alone. I feel Canonical want to be looking at this if upstream is adamant on leaving it out, as it really is something of a problem for new users.

---

### Post by warpasylum on 2009-05-05
True, the settings are also a pretty normal and expected function of screensavers. I like gnome alot but these are the shortcomings that make me wonder about going back to kde. Ubuntu should definitely look into putting this functionality back in as the workarounds are not at all friendly to new users.

---

### Post by MyR on 2009-05-05
It's very irritating to me too.  Sure, it's free, but seriously does that mean the quality has to be horrible?  Back in the days of Breezy Badger, the screensavers on gnome were decent because they could be configured.

Now we just have scrolling text we can't change, images we can't change, and some stupid graphics tricks that look like they were programmed on a graphing calculator during lunch hour. 80-90% of the screensavers are pathetic, like the retarded ants walking in circles inside globes.  WTF??

/rant

---

### Post by warpasylum on 2009-05-05
I'm just trying to get my head around a LINUX app that takes away the ability to personalize and configure it to suit your needs. That's the biggest reason I chucked windows and started messing around with linux in the first place. I don't need people to tell me what I can or can't do on my own system. I really don't understand the point in taking away all the config options of any program. One configuration doesn't fit all... hint to the Gnome folks :). Please bring back the config options.

---

### Post by bschultzjames on 2009-05-26
My biggest thing with using the xscreensaver is the fact that I can select multiple screensavers to use and rotate during screensaving.  

It would be nice to see the option[s] of the checkboxes and fully customizable settings added to future builds of the gnome-screensaver.

In the meantime, is there any way to completely disable the gnome-screensaver?  It would be convenient to just have the xscreensaver so I don't have to keep re-opening and re-allowing the xscreensaver to override gnome-screensaver.


Thanks everyone!

---

### Post by MyR on 2009-05-26
> **bschultzjames said:**
> My biggest thing with using the xscreensaver is the fact that I can select multiple screensavers to use and rotate during screensaving.  

It would be nice to see the option[s] of the checkboxes and fully customizable settings added to future builds of the gnome-screensaver.

In the meantime, is there any way to completely disable the gnome-screensaver?  It would be convenient to just have the xscreensaver so I don't have to keep re-opening and re-allowing the xscreensaver to override gnome-screensaver.


Thanks everyone!

how about removing gnome-screensaver?

---

### Post by leehach on 2009-08-17
> **warpasylum said:**
> Hey guys,
     Trying to update the paths for the pictures that the Ripples screensaver uses. I removed the pictures that I don't want used from /usr/share/backgrounds which is where it grabs them from. Now when i run the screensaver it still looks for the files i removed and shows them as a broken link, i.e. flaming t.v. and color bars pic. Any ideas on how to fix? Thanks. By the way, I'm still using Gnome screensaver.
I'm also using the Gnome screensaver, but changed the path for xscreensaver image files. Edit the setting imageDirectory in the file /home/<username>/.xscreensaver. For example, on my system I created a directory called /data/Screensaver just for screensaver images.

A version of this file with default settings exists as /etc/X11/app-defaults/XScreensaver.

This info by the way is courtesy of [https://help.ubuntu.com/community/CorporateUbuntu]("https://help.ubuntu.com/community/CorporateUbuntu"). I stumbled across it via Google while trying to deal with the same screensaver stuff as everyone else here.

I agree with everyone else here that the configuration settings available via Xscreensaver should be in the Gnome Screensaver Preferences dialog. But after 23meg's guide to replacing gnome-screensaver with xscreensaver, I switched back because the xscreensaver lock screen feature was slow (and ugly), and I have multiple users on the home computer who are often switching between accounts. I'll just hand edit the .desktop files in /usr/share/applications/screensavers.

Now if only I could get the Picasa screensaver to work...

---

### Post by sad1sm0 on 2009-12-02
So this is a pretty old problem I see.  I'm trying to get the barcode screensaver to display thru gnome-screensaver, but all i get is a blank screen.  Checked the rest of the xscreensaver(s) and they all seem to work but this one.  Barcode previews in screensaver-demo, can anyone confirm this screensaver not working outside of xscreensaver?  if so, any explanation?

---

### Post by Nadurru on 2009-12-16
Well I must be a new guy or something. I tried to follow your instructions and it didn't get me anywhere. When I copied the command line string and thrie to find the theme folder it wasn't there. I went into usr/share/gnome-screensaver and there is no theme folder just 2 files "gnome-screensaver-preferences.ui and lock-dialog-default.ui

Any idea where my theme folder got off to? 

Also since I'm here, when I boot now Gnome-screensaver is open and up in the upper left hand corner waiting to be closed. I have to manually close it and start Xscreensaver. 

I have no Idea why it's doing that or why Xscreensaver isn't starting when I boot.

Nadurru

---

### Post by rCXer on 2009-12-16
Try the [other guide](http://ubuntuforums.org/showthread.php?t=195557).  It is much more detailed but longer.

---

### Post by Nadurru on 2009-12-16
I did try the other guide. Still I have gnome-screensaver in the corner and I have to close it and start xscreensaver.

Nadurru

---

### Post by rCXer on 2009-12-16
Try uninstalling gnome-screensaver.  That should kill it for good.

---

### Post by Cyeb on 2010-03-23
> **Nadurru said:**
> Well I must be a new guy or something. I tried to follow your instructions and it didn't get me anywhere. When I copied the command line string and thrie to find the theme folder it wasn't there. I went into usr/share/gnome-screensaver and there is no theme folder just 2 files "gnome-screensaver-preferences.ui and lock-dialog-default.ui

Any idea where my theme folder got off to? 

Also since I'm here, when I boot now Gnome-screensaver is open and up in the upper left hand corner waiting to be closed. I have to manually close it and start Xscreensaver. 

I have no Idea why it's doing that or why Xscreensaver isn't starting when I boot.

Nadurru

I had a bit of trouble with this too, but I found the solution.  (To your first question about where the screensaver option file went, that is.)

1.  Open a terminal and type "locate [screensaver]"
2.  You'll see one of them ends in ".desktop".  That's the file you want to edit.
3.  Type "gksudo gedit [path to file goes here]"
4.  Edit as you please.

:)

---

### Post by jockovonred on 2010-05-30
> **Cyeb said:**
> I had a bit of trouble with this too, but I found the solution.  (To your first question about where the screensaver option file went, that is.)

1.  Open a terminal and type "locate [screensaver]"
2.  You'll see one of them ends in ".desktop".  That's the file you want to edit.
3.  Type "gksudo gedit [path to file goes here]"
4.  Edit as you please.

:)

i stumbled across making this change myself and then i read your post which confirmed what i modified (was looking to configure the easter egg in xmatrix).  i did this for karmic so it will probably apply to future distros too.  i didn't install xscreensaver but stuck with gnome-screensaver.

came across this info too:
[http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions](http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions)
[http://xfx.net/utilities/sss/download.htm](http://xfx.net/utilities/sss/download.htm)
[http://ubuntuforums.org/showthread.php?t=198809&page=3](http://ubuntuforums.org/showthread.php?t=198809&page=3)
[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

---

