---
title: "HOWTO: change how Nautilus parses file types"
date: 2007-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by svivian on 2007-11-09
After searching around these forums a bit I finally found a solution to problems I was having with Nautilius.

[SIZE="4"]_The problem:_[/SIZE]

Nautilus reads files in order to determine the file type, rather than basing it off the extension. While in theory this is a great idea, it fails in a couple of places. Notably with plain text files, many scripts/programs are parsed incorrectly. For example, a PHP script is only parsed as such if the first line contains <?php which is not always the case. This causes a few unwanted effects like opening with different apps by default and files jumping around in the file list window when ordered by type.

The solution: Change how Nautilus parses the file types! The rules it uses are all listed in the file **/usr/share/mime/packages/freedesktop.org.xml**. I've provided two solutions: the former for people familiar with XML and Linux in general; the letter being more detailed.

[SIZE="4"]_Quick solution:_[/SIZE]

1. Back up the freedesktop.org.xml.
2. Open the freedesktop.org.xml file as super-user.
3. Find the mime-type that your file is being incorrectly parsed as.
4. Remove the <magic> element and its contents, or alternatively change the <match> elements.
5. Run **sudo update-mime-database /usr/share/mime**

[SIZE="4"]_Detailed solution:_[/SIZE]

Don't forget to back up first:
```
sudo cp /usr/share/mime/packages/freedesktop.org.xml /usr/share/mime/packages/freedesktop.org.xml.bak
```

You can open the file with the command (& is so you can continue using commands with the file open)
```
sudo gedit /usr/share/mime/packages/freedesktop.org.xml &
```

If you search for "*.php", you should see a section similar to this. To keep it short I've removed the translations but you should leave them in the file.
```
  <mime-type type="application/x-php">
    <sub-class-of type="text/plain"/>
    <comment>PHP script</comment>
    <comment xml:lang="az">PHP skripti</comment>
    [... more translations here ...]
    [b]<magic priority="80">
      <match value="&lt;?php" type="string" offset="0:64"/>
    </magic>[/b]
    <glob pattern="*.php"/>
    <glob pattern="*.php3"/>
    <glob pattern="*.php4"/>
  </mime-type>
```

The part in bold is what will decide the type. For each mime type, it is listed in <magic> tags. So for your chosen file type, all you have to do is remove the <magic> element and its contents.

Once you're done, save the file and run this command:
```
sudo update-mime-database /usr/share/mime
```

The same process should apply for all file types. To stop PHP files being parsed as HTML documents, you will need to remove the magic element from the HTML mime type as well.

Hope this is useful to people!

---

### Post by mrprowse on 2008-03-27
Thanks for the awesome walkthough! Ubuntu kept warning me that my Javascript files were really MATLAB files trying to secretly pwn me. Your tip did the trick!

:-j
Josh

---

### Post by arkmundi on 2008-05-12
Likewise - thanks!  I recently ported from Windows XP, so am very new to Ubuntu, and trying to get a handle.  A lot of my ported files where showing up as mime-type x-vhdl, a very wierd file type "Very High Speed Integrated Circuit."  Someone was definitely very high when they included the "magic" in the freedesktop.org.xml so that files having a "--" show up as this file type.  This can be really confusing for people coming over to Ubuntu and Nautilus - how can this misapplication be reported so its removed from future versions??  Also, the sudo update-mime-database didn't change file types on the fly, but rebooting did; am on Ubuntu 7.10.

---

### Post by martin_lindhe on 2010-01-11
thanks so much for posting that!

---

### Post by Ryborg on 2011-02-08
Is there some way to totally disable the mimetype "magic" that is going on?  I would like things to just open based on file extension, even if I might open a mislabeled file.

---

