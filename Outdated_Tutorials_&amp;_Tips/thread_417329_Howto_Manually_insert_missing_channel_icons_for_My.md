---
title: "Howto: Manually insert missing channel icons for MythTV"
date: 2007-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by barney_1 on 2007-04-21
[SIZE="5"]This guide will show you how to manually insert station icons for stations that did not get automatically downloaded using the mkiconmap.pl method of icon acquisition.[/SIZE]

**This guide assumes that you have MythTV and PHPmyadmin both installed and running.**

If you need help with the prerequisites please visit these links:

**Installing MythTV:**
[https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV")
**Installing PHPmyadmin:**
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_for_Apache_HTTP_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_for_Apache_HTTP_Server")

**[COLOR="Red"]It would be a good idea to make sure you have a recent backup of your MythTV database (mythconverg) before doing ANY editing:[/COLOR]**
```
mysqldump -u root -p mythconverg -c > mythtv_backup.sql
```
[INDENT]Read more about backing up your database:
[http://www.mythtv.org/wiki/index.php/Backup_your_database]("http://www.mythtv.org/wiki/index.php/Backup_your_database")[/INDENT]
[B][SIZE="4"]

Now let's get started:[/SIZE][/B]


**Step 1: You should already have used the mkiconmap.pl method to install the majority of your icons:**
[INDENT]Follow the community documentation:
     [https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons")[/INDENT]


**Step 2: Log in to PHPmyadmin and select the MythTV database:**
[INDENT]In a browser enter the following address, replace "localhost" with your backend IP address:
```
http://localhost/phpmyadmin
```
Enter "root" for username and the root password for your mySQL database as prompted.

From the drop-down box at the left (labeled "database") choose "mythconverg" which is the MythTV database.[/INDENT]


**Step 3: Select the channel table, browse, and sort by channel number:**
[INDENT]Once you are viewing "mythconverg" a new list will appear in the left pane.  Click on "channel".

In the right window, click on the "browse" tab at the top.

In the list on the right hand window, click on "channum" to sort by channel number.[/INDENT]


**Step 4: Back up your channel table before making any changes!**
[INDENT]Click on the "export" tab at the top of the right hand window.

Scroll to the bottom and make sure to put a check mark in the box marked "save as file".

Click the "go" button on the bottom right.  You will be prompted for a filename (default should be "channel.sql") and location.

Once the file has been saved click on the "browse" tab and then sort the list by clicking the "channum" column label.[/INDENT]


**Step 5: Discover icon locations and acquire the icons you wish to manually insert.**
[INDENT]In the right hand pane of PHPmyadmin find the column labeled "icon".  This lists what icon is assigned to each channel.  Any lines that do not have a file name and path do not have an icon assigned to them.

Make note of the location that the icons are being stored.  Here is an example of an icon entry:
```
/home/mike/.mythtv/channels/tbs.jpg
```
From this you can tell that my icons are stored in this directory:
```
/home/mike/.mythtv/channels/
```
I just want to place a generic icon in all of the channels without one so that I don't have channels without a picture next to their call letters.  For this I downloaded an icon of a television using Goole Image search:
[http://images.google.com/]("http://images.google.com/")

Once you have your image (or images) save it to your icon directory.  Here is my generic icon location:
```
/home/mike/.mythtv/channels/genericTV.gif
```[/INDENT]


**Step 6: Insert image location into PHPmyadmin:**
[INDENT]Go back to PHPmyadmin.  Find a line that has no entry in the "icon" column and click the pencil icon on the left side of that line.  This will take you to an edit window.

In the "field" column find the entry labeled "icon".  Follow this to the right and click in the text box of the "value" column.  Input the icon filename and path for this channel.  I am using one generic image for all unassigned channels so this is what my icon value will be for all of these channels:
```
/home/mike/.mythtv/channels/genericTV.gif
```
Click the "go" button to save this value.

Repeat this step for each channel that you want to add an icon to.[/INDENT]


**Step 7: That's it!  Close your browser window and restart your frontend.  You should now have channel icons for all of your channels.**



**[SIZE="2"]How to restore you "channel" table in the event of an error:[/SIZE]**
[INDENT]If you are having problems that you didn't have before working with your database you may have inadvertently damaged your channel table.

A:  Follow steps number 2 and number 3 from above.
B:  Drop the damaged channel table by clicking the "drop" tab at the top (make certain the very top line of this  window says "Table: channel").
C:  Import your saved table by clicking the "import" tab at the top, selecting your backed up channel table (channel.sql) and clicking the go button on the bottom right.[/INDENT]


**Special Note:**
I found that a few channels had icons assigned, but the icon was basically just a transparent file, no image at all.  I edited these using Step 5 and changed the image to my generic image.

---

