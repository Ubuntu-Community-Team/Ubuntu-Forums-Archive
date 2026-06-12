---
title: "locating an application"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by renbri on 2014-12-24
All the Noddy's guides to Ubuntu I've looked at tell me to use the Dash to find a file or an application. 
But this doesn't seem to tell me where the app is actually located.
As an example, I just downloaded a little game called Kolf. I thought I might put it on the desktop as I've done with a couple of others, i.e. locating them via Files-Computer/usr/share/applications and then copying and pasting onto the desktop. But Kolf -having turned up on the Launcher- does not seem to be in /usr/share/applications folder. 
Since I am going through exactly the same procedure as I did with other games -e.g. dreamchess- I'm baffled.
Previous advice hinted that the name might have changed so I searched for the symbol (a white circle in a black rectangle) but no dice. 
Where did I go wrong?

---

### Post by Dreamer Fithp Apprentice on 2014-12-24
"applications" is a misleading name for that directory. The files in /usr/share/applications aren't the applications themselves but "desktop" files, so called because many people, like you, like to put them on their desktop. They are small text files that contain information useful to applications that automatically maintain a menu by adding entries for newly installed applications (or at least new applications that are menu friendly and HAVE desktop files. Some graphical file browsers make this really hard to understand by trying to be too clever by half and refusing to show the actual filename of the desktop files. I hate the attitude that leads programmers of basic gui utilities to do crap like that. If you know how to start the game from the command line you can make your own desktop file for it. You might find this easier to do if you work from the command line since at least bash won't hide the filename from you. But you want to copy one of the desktop files in in /usr/share/applications and rename the copy kolf.desktop. Then open it with a text editor like gedit, find the line beginning "Exec=" and replace the command for whatever program the model was for with the command that starts Kolf. Then find the line that begins "Name=" and replace the name there with "Kolf". No space following the = in either case.
If you don't know how to start it from the command line, and the obvious possibilities like "kolf" or "Kolf" don't work, you might try using a file search utitlity like gnome-search-tool to look for files with kolf in the name. There will probably be an executable in some directory named "bin". If so "path/to/bin/kolf-executable-file" might be the way to start the game from the command line and if it is, you can use that in the desktop file.

---

### Post by vasa1 on 2014-12-24
> **renbri said:**
> All the Noddy's guides to Ubuntu ...
Could you share information about Noddy's guides. I haven't come across this resource as yet.

---

### Post by ajgreeny on 2014-12-24
Obvious commands to try are 
```
whereis kolf
which kolf
```The first will give you lots of paths to kolf (if that is the correct name) and the second will show you the path to the executable file.

For all files with that name in either upper or lower case you can try ```
locate -i kolf
```which might give you clues.

---

### Post by deadflowr on 2014-12-24
kolf is a kde-like(I don't know what else to call it) application.
Typically kde-type apps might have there own, bizarre paths for desktop files.
I would use something like dpkg-query to look over the list of installed files, and possibly go a little further and grep.
Something like
```
dpkg-query -L kolf
```
Which will list everywhere that kolf has a file associated with it on the system.
You can go a further and cut that down to only where any file associated with a desktop by piping grep
like this
```
dpkg-query -L kolf | grep desktop
```
My guess is that you'll have some entries for stuff like kde4 listed.
Quite typical as kde goes it's own way a lot of the time.
Where as other Desktops like Gnome, or Xfce have a more standard(y) way of doing it. IMHO

(FYI if you have installed synaptic package manager, the output for dpkg-query -L is easy to find by highlighting the package > click on Properties > go to Installed Files in the Properties dialog box)

---

### Post by renbri on 2014-12-24
Strewth! I'm overwhelmed -not to say intimidated- by the complexities in these replies. A lot of it went over my head but I had a play with some of the command line stuff you all suggested and eventually found the GUI elements I was seeking. Having learned that Linux commands and file names are case sensitive, I was careful to use the word "Kolf" -which is how it appeared in the Software Centre- but that only drew blanks; when I switched to "kolf" I got lines and lines of information and was eventually able to pick out the names of the subdirectories that mattered and thence find my way through the Unity menus to the appropriate places where the Kolf game resided. Interestingly I could access it both through usr/share and through usr/games, the latter being a colourless icon that immediately started the game!
These applications and "packages" seem to be scattered in ways quite baffling to the tyro.
I guess I'm trying to run before I can walk but the scenery is fascinating, even if the way ahead looks steep and rocky, and your help has been tremendous.
Many thanks, boffins, and a bonzer yuletide to you all.

---

### Post by Dreamer Fithp Apprentice on 2014-12-25
> **vasa1 said:**
> Could you share information about Noddy's guides. I haven't come across this resource as yet.Let me hazard a guess - OP can confirm or refute if he checks in - given the plural construction I suspect he just means guides aimed at less advanced students, primer level stuff, like the well-known book series "Dummies' Guide to . . . ". I think "noddy" is a briticism meaning "stupid person". You know them there Limies never have learned to speak plain Amurican.

@ ajgreeny & deadflowr: Interesting posts as always. I learned from both of them. I'd never heard of "which". I wonder how many bash commands there actually are and if there is an alphabetical list with brief descriptions somewhere.

@ renbri:
Glad you got it working. From what you say I picture you navigating to /usr/games and double clicking on some file in there to start your game. Sounds a bit less than ideal convenience-wise. If that's the case and if you'd rather be able to double click something on the desktop, you might try to right click on that file and click "properties". If the size is very small that is probably a desktop file. My largest desktop file is under 8 kilobytes and most are less than a kilobyte. It would probably also say something like "desktop configuration file" in the properties box. If you right click on it and open it with an editor and it has a lot of short lines starting "something=" ("something" being anything), that's what you want. Right click on it and copy it. Then paste the copy on your desktop. If you'd rather navigate to the desktop with your file browser, it's at /home/your_user_name/Desktop.

If you consider this issue completely solved, it is good form to click the button above your post that is labeled "thread tools" and then click "mark solved" in the drop down menu. It can save other people wasted effort.

And finally, a Cherry Christmas and a Nifty New Year to you as well, and to all here, and to all a good night. :-)

---

### Post by ajgreeny on 2014-12-26
@ Dreamer Fithp Apprentice
There are many places you can get info and full man details of the complete range of Linux bash commands, eg.
[Linux commands]("http://www.ss64.com/bash/") 

Click on any of those command on the left and you are taken to an html page of the manual output

---

### Post by Dreamer Fithp Apprentice on 2014-12-26
> **ajgreeny said:**
> @ Dreamer Fithp Apprentice
  . . . [Linux commands]("http://www.ss64.com/bash/") Thanks, Ajgreeny! That is a supercool resource. I can browse it and learn commands I never suspected existed.  Best of the season, to you!

---

