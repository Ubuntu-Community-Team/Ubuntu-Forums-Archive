---
title: "Gnome/Nautilus most used shortcuts"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by sica07 on 2008-05-07
Howdy! I thought that it would be useful to post a practical selection of shortcut keys for GNOME (the Desktop Environment) and Nautilus (the File Manager) and some information about customizing shortcut keys in Ubuntu. I wrote it especially for Ubuntu beginners, but I hope it will prove useful for all.  

_**1.GNOME/Nautilus shortcut keys:**_

**Ctrl-H**: show hidden files
**Ctrl-N**: new window
**Ctrl-Shift-N**: create new folder
**Alt-Home** : jump to home folder
**Alt-Enter **: file / folder properties
**F9 **: toggle side-pane
**Alt-F1** : launch applications menu
**Alt-F2** : launch "run application" dialogue
**Ctrl-Alt** - Right/Left arrow : move to the next virtual  desktop
**Ctrl-Alt-Shift** - Right/Left arrow : take current window to the next virtual desktop
**Ctrl-Alt-D**: minimize all windows, and gives focus to the desktop. 
**Alt-Tab**: switch between windows. When you use these shortcut keys, a list of windows that you can select is displayed. Release the keys to select a window. 
**Ctrl-Alt-Tab**: switch the focus between the panels and the desktop. When you use these shortcut keys, a list of items that you can select is displayed. Release the keys to select an item. 
**Ctrl-Alt-L**: lock the screen 
**Ctrl-L**: shortcut for opening locations-by default the path is the home folder*
**/** : same as Ctrl-L but has the root (/) as default path* (shortcut found on [_here_]("http://fosswire.com/2007/12/06/open-any-folder-from-your-gnome-desktop/"))
 * *both shortcuts can be used while you are on the desktop (no window active)*

***Ctrl-T** : move to trash (in Nautilus)*
*Quite dangerous key combination because many of us are used to press these keys in order to open a new tab. Because we all delete items using the Delete key, I recommend to deactivate this shortcut key. To do that, go to System » Preferences »  Appearance » Interface. Select Editable menu shortcut keys and close the dialog box. Click on the Edit menu in the File Browser. Click the Empty Trash item (it has Ctrl-T as the keyboard shortcut) Press the Delete key to get rid of the shortcut.*
You can find all GNOME shortcut keys  [_here_]("http://library.gnome.org/users/user-guide/latest/keyboard-skills.html.en")

[U][B]2.How to create a custom hotkey to launch whatever application you want in GNOME:

[/B][/U]Open "gconf-editor" as the user as you're logged in in GNOME (typing gconf-editor in the terminal or "Run Application").
Go to apps > metacity > keybinding_commands
Here we have a list of twelve slots for commands. Double click on e.g. "command_1" 
In Key Value Type in the name of the application you want to launch.
Go to apps > metacity > global_keybindings 
Double click on e.g. "run_command_1" 
Change the key value to whatever key combination you like.Press "Ok".


_**3.How to create/change GNOME shortcuts:**_

Click on System > Preferences > Keyboard Shortcuts 
Click the action in the list and press Enter. 
Press the new key or key combination you want to assign to the action. (To clear a shortcut, press the Backspace key)

**_4.How to use the Windows-keys:_**
Go to System>Preferences>Keyboard.
Go to the Layouts tab and press the Layout Options button.
Open the Alt/Win key option.
Select the &#8220;Super is mapped to the Win-keys&#8221; behaviour.
Close the windows.
Now, that we have set the key behaviour, let&#8217;s make some Windows like shortcuts.
Go to System>Preferences>Keyboard Shortcuts.
Go to Window Management section.
Search for &#8220;Hide all windows and focus desktop&#8221;. Click on it.
Press the <WIN><D> combination.
Close the window and test your new shortcut.

Hope it helps.;)

---

### Post by diaa on 2008-05-07
Nice list, thanks, I didn't know about Ctrl-L on the desktop, pretty handy.

It's worth mentioning that those related to nautilus are configurable (via System > Preferences > Keyboard Shortcuts):
**Ctrl-Alt** - Right/Left arrow
**Ctrl-Alt-Shift** - Right/Left arrow
**Ctrl-Alt-D**
**Alt-Tab** 
**Ctrl-Alt-Tab**
**Ctrl-Alt-L**

---

### Post by sica07 on 2008-05-11
Post updated!
I added a section about how to make shortcuts with the <WIN> key. ;-)

---

### Post by jive_turkey on 2008-05-15
Two releases ago there was the command:

Ctrl+Alt+[Up Arrow]

It would zoom out and show all the open applications, it was similar to something that you can do in Apple OSX and it has since dissapeared. If anyone knows what I'm talking about and can help me get that shortcut back I would really appreciate it. 

Thanx

---

### Post by Phrawm48 on 2008-05-24
> **diaa said:**
> 

It's worth mentioning that those related to nautilus are configurable (via System > Preferences > Keyboard Shortcuts):


Well, sort of...  Gnome's Keyboard Shortcuts tool clearly allows the definition of an existing shortcut to be more or less readily added or changed, but doesn't seem to allow new shortcuts to be create or defined.

Is there a straightforward way to create a new keyboard shortcut?  I'd prefer not to have to experimentally hand-edit a text-based configuration file...

Cheers & thanks,
Ric
SFO

---

### Post by sica07 on 2008-05-25
You could use gconf-editor. See the second point on my post, "How to create a custom hotkey to launch whatever application you want in GNOME".

---

### Post by badchoice on 2008-05-27
Is there a way using this bindings to launch my application with the filename as a parameter, os with the folder as a parameter??

I'm developing quicklook for linux and it will be very useful!!

Here you can see my project:

[http://www.youtube.com/watch?v=fo09GRwbokU](http://www.youtube.com/watch?v=fo09GRwbokU)
[http://sourceforge.net/projects/gloobus](http://sourceforge.net/projects/gloobus)

[http://ubuntuforums.org/showthread.php?p=5017478#post5017478](http://ubuntuforums.org/showthread.php?p=5017478#post5017478)

Thanks!

---

### Post by diaa on 2008-05-27
> **badchoice said:**
> Is there a way using this bindings to launch my application with the filename as a parameter, os with the folder as a parameter??

I'm developing quicklook for linux and it will be very useful!!

Here you can see my project:

[http://www.youtube.com/watch?v=fo09GRwbokU](http://www.youtube.com/watch?v=fo09GRwbokU)
[http://sourceforge.net/projects/gloobus](http://sourceforge.net/projects/gloobus)

[http://ubuntuforums.org/showthread.php?p=5017478#post5017478](http://ubuntuforums.org/showthread.php?p=5017478#post5017478)

Thanks!

Yes, try
```
gnome-text-editor `zenity --file-selection`
```and
```
nautilus `zenity --file-selection --directory`
```*Note that these are backticks, not ordinary single quotes*

Obviously this needs zenity installed to work

---

### Post by badchoice on 2008-05-28
It is not exactly what I was looking for.
I want to get the filename parameter without a dialog box, like if you press ctrl+t that it sends the file to the trash without a dialog box!

---

### Post by EFobes on 2008-06-17
I am trying to find/create a keyboard shortcut for the keyboard layout. I have to write French so I switch between the French and English layout quite often. Now, the only way I know to do it is to click the icon on the panel. (Keyboard Shortcuts doesn't mention this option)

---

### Post by diaa on 2008-06-17
> **EFobes said:**
> I am trying to find/create a keyboard shortcut for the keyboard layout. I have to write French so I switch between the French and English layout quite often. Now, the only way I know to do it is to click the icon on the panel. (Keyboard Shortcuts doesn't mention this option)

You have to do this from layout options tab

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/gnome_hotkey_to_switch_keyboard_layout](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/gnome_hotkey_to_switch_keyboard_layout)

---

### Post by zajc on 2009-04-16
Is there any shortcut or possibility to bind keys for sorting files by name, date, size, type instead of mouse clicking?

---

