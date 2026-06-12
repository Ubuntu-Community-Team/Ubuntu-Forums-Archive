---
title: "How do you delete files"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by Colin_Reece on 2014-05-05
I searched online but from what I found I have to input command lines to delete a file, I am new to Ubuntu and thought the right click of the mouse would be enough but no.
I tried highlighting the file and using the delete key but that didn't work either, so is there something I'm missing or is it inserting code to simply dlete a file? :(

---

### Post by HermanAB on 2014-05-05
Howdy,

You can only delete files that belong to you.  Files that do not are likely best left alone.

---

### Post by Colin_Reece on 2014-05-05
Hmm!  I downloaded a file twice by mistake and I also wanted to delete a picture, so does that mean I'm stuck with them, I can see me going back to using Windows, a lot os simple tasks are not that simple on Ubuntu.

---

### Post by slickymaster on 2014-05-05
See this tutorial: [DeletingFiles]("https://help.ubuntu.com/community/DeletingFiles")

---

### Post by texpat on 2014-05-05
In the file browser you can right-click the filename/icon to get a context menu. About halfway down it says "move to the rubbish bin".

You get the same result highlighting the filename/icon and then hitting "del" on your keyboard.

From the rubbish bin you can restore the file in case you change your mind about deleting it. Otheriwse you can "empty rubbish bin" to permanently delete the file.

On the command line you go

```
rm /path/to/file/delete.me
```

This deletes without first moving the file to the rubbish bin.

---

### Post by 3rdalbum on 2014-05-05
> **Colin_Reece said:**
> I searched online but from what I found I have to input command lines to delete a file, I am new to Ubuntu and thought the right click of the mouse would be enough but no.
I tried highlighting the file and using the delete key but that didn't work either, so is there something I'm missing or is it inserting code to simply dlete a file? :(

Which file, and where is it? You can right-click and delete files that belong to your user account. Any files owned by Root are system files and best left alone unless you know what you are doing. You can't "just" delete a root-owned file. It doesn't belong to you!

If you are 100% sure you need to delete it, then you need to run your file manager as root. This is easy to do, but I will let you do the research yourself to find out how to do it...

(Or you can use the command-line to delete it as root, either way is fine).

---

### Post by Colin_Reece on 2014-05-05
No sorry didn't get any option to delete to the rubish bin, all I get is the option to open it.
I'm on Ubunto 14.04 if that is any help.

---

### Post by coffeecat on 2014-05-05
> **Colin_Reece said:**
> No sorry didn't get any option to delete to the rubish bin, all I get is the option to open it.
I'm on Ubunto 14.04 if that is any help.

If you right-click on a file in your home folder or on the desktop in Ubuntu 14.04, you should see a context menu like this with "Move to the Rubbish Bin" about halfway down. "Rubbish Bin" may be replaced with "trash" or another string depending on your location. The first line in the context menu will vary according to the type of file - I clicked on an image file as an example.

[center][img]http://ubuntuforums.org/attachment.php?attachmentid=252881&d=1399287061[/img][/center]

What exactly are you seeing and where is the file that you are clicking on?

[ATTACH=CONFIG]252881[/ATTACH]

---

### Post by Colin_Reece on 2014-05-05
Ah!  That did it, I wasn't in the home folder to view the files, thank you.

---

### Post by coffeecat on 2014-05-05
@Colin_Reece, in fact Ubuntu works almost exactly the same way as Windows for deleting files in the GUI. You can move to trash/rubbish bin/recycle bin from the right-click context menu. Or you can highlight the file and press the del key to move to trash.

Or if you want to hard delete, highlight the file to be deleted in the file browser, and press shift-delete. You will be prompted with a "are you sure?" or words to that effect type prompt in both Ubuntu and Windows, and if you then OK it, the file will be deleted, bypassing the trash/recycle bin.

---

