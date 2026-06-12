---
title: "HOWTO: Automatically sync Google Calendar to iPod"
date: 2007-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by hackle577 on 2007-11-17
**[SIZE="3"][COLOR="Red"]UPDATE:[/COLOR] I cannot get this to work in Hardy due to several complicated (and probably conflicting) autorun options. If you get it functioning somehow, please PM me.[/SIZE]**

If you&#8217;re constantly on the go (and who isn&#8217;t these days?), you know that having an up-to-date schedule with you at all times is a valuable asset. Some people keep their calendars in day planners, others use their PDA&#8217;s or cell phones, but for the oddballs out there who want to keep their schedule on their iPod too, here&#8217;s how:

[SIZE="4"]1.[/SIZE] Browse to your Google Calendar. Go into **Settings**, then the **Calendars** tab, and click the name of the calendar you want to sync. At the bottom, to the right of **Private Address**, you'll see a green **ICAL** button.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67343&stc=1&d=1209229650[/IMG]

Right-click that button and select **Copy Link Location**.

[SIZE="4"]2.[/SIZE] Open up your favorite text editor and type &#8220;wget -N&#8221; and then paste your iCal URL. The end result should look something like this:

    ```
wget http://www.google.com/calendar/ical/emailaddress%40gmail.com/private-hash/basic.ics
```

[SIZE="4"]3.[/SIZE] On the next line, type this:

```
mv -f basic.ics /path/to/your/ipod/Calendars
```

You will need to replace that fake path with the actual path to the Calendars folder on your iPod, which may be something like &#8220;/media/ipod/Calendars&#8221;.

[SIZE="4"]5.[/SIZE] Save the text file as &#8220;syncgoocal.sh&#8221;.

[SIZE="4"]6.[/SIZE] Now we need to move the script and let it run as a program. In terminal, type these two commands:

```
sudo mv syncgoocal.sh /usr/local/bin
sudo chmod +x /usr/local/bin/syncgoocal.sh
```

[SIZE="4"]7. [/SIZE]Now that we&#8217;ve created the script, we need to set it to run automatically when you plug in your iPod. Go to **System > Preferences > Preferred Applications**. Under the **Multimedia** tab, you should see and entry for a **Multimedia Player**. Change the combo box to "Custom" and type:

    ```
/usr/local/bin/syncgoocal.sh
```

Then click close.

-------------------------------------------

Your iPod&#8217;s calendar will now be synced to your Google Calendar every time you plug it in. Enjoy! Credit goes to Peter Howe for [the original idea]("http://www.xenzero.com/blog/2007/10/06/sync-google-calendar-with-ipod-on-ubuntu-linux/").

[SIZE="4"]To undo:[/SIZE] Simply run "sudo rm /usr/local/bin/syncgoocal.sh" and remove the script's entry in the **Removable Drives and Media** options box.

**[COLOR="DarkOrange"]Tested on Ubuntu Gutsy 64-bit and an iPod Video (5th generation)[/COLOR]**

---

### Post by ftreprez65 on 2008-04-22
hey, i try to type in that code, and when i get to the part where i have to type in mv -f basic.ics /path/to/your/ipod/Calendars, i get this error:
mv: cannot stat 'basic.ics': no such file or directory

how do i fix this?

---

### Post by hackle577 on 2008-04-22
I did a little searching around and I can't find a specific remedy for the "cannot stat" problem. I think it has something to do with permissions, which may mean you perhaps don't have the correct permissions to write to your iPod.

Let me do some more looking and see what I can come up with...

---

### Post by zi99y on 2008-05-27
Thanks hackle577, this is great, I didn't know google calendar could output in ipod format - how simple! 

I'm now wondering if there's a way of syncing the "To Do's" from somewhere - not sure how they are used normally - itunes/outlook?? 

ideas?!

---

### Post by hackle577 on 2008-05-27
The notes feature can only use plain text files (.txt). Just drop them in the Notes folder on your iPod and you'll be able to access them next time you use it. So if you wanted to make a to-do list sorta thing, just make a .txt file with a list inside, like:

```
Milk
Eggs
Chicken
Cheese
```

---

### Post by hackle577 on 2008-05-27
If you want to sync a to-do list from somewhere, I imagine you'd have to output your list as some sort of file, then strip away any extra encoding to get just text, then transfer it over. That shouldn't be too hard to do in a bash script.

---

### Post by ma65p on 2008-08-28
> **hackle577 said:**
> I did a little searching around and I can't find a specific remedy for the "cannot stat" problem. I think it has something to do with permissions, which may mean you perhaps don't have the correct permissions to write to your iPod.

Let me do some more looking and see what I can come up with...

The problem is because you are in the wrong directory."syncgoocal.sh" is located in the Calendars folder in your ipod. 'cd' there, then move, or just use nautilus and copy then paste (You may need to have root permission). Hope that helps

---

### Post by redandgray on 2008-11-03
In case it's not obvious, this is not a two-way "sync".  Any calendar changes made on your iPod will be lost the next time you connect to your computer.

Also note: this will not work on the iPod Touch, which has no USB disk access option.

---

### Post by Floola on 2008-12-12
Google calendar synch was added to Floola 4.2. Type username and password and all online calendars will be listed, which can then be synched just with a single click.

[http://www.floola.com](http://www.floola.com)

Enjoy,
Tomas

---

