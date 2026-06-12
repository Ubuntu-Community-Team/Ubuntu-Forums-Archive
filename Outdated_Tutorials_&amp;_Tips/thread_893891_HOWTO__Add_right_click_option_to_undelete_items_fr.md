---
title: "HOWTO:  Add right click option to undelete items from the trash in gnome"
date: 2008-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by glennric on 2008-08-18
!!!! This is for Hardy (and possible before) only.  This feature is now fully implemented in the nautilus in Intrepid !!!!

In the release of Gnome shipped with Hardy, you can delete things to the trash from Nautilus, but you can not undelete or recover them to their original location.  However, Gnome does store this information.  Rumor has it that the undelete from trash option was in the pre-released version of Gnome, but the developers removed it right before it was released.  I guess they felt it was not ready yet.  I have also heard that this will be in the next release of Gnome.  So this howto will be obsoleted then.  For those who want the undelete option now -- here you go.

This tutorial will tell you how to add an option to the menu that appears when you right click on items in the trash to undelete or recover the item to its original location.  (Note that you can also open the trash in nautilus and click and drag files from the trash to another location if desired.)

**First** install the packages "zenity", "gvfs-bin", and "nautilus-actions".  You can do this using synaptic or the command line:
```
sudo apt-get install zenity gvfs-bin nautilus-actions
```

**Second** download the attached gzipped script "undelete-trash.gz" to your desktop, and run the following command from a terminal.
```
gunzip ~/undelete-trash.gz && mkdir -p ~/bin && mv ~/undelete-trash ~/bin && chmod +x ~/bin/undelete-trash
```

**Third** configure nautilus-actions.  
Go to System-Preferences->Nautilus Actions Configuration
Click "Add" and set the options under the "Menu Item & Action" tab as in the following image:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=82434&stc=1&d=1219418909[/IMG]

Then set the options under the "Conditions" tab as in the following image:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=82041&stc=1&d=1219100914[/IMG]

Then set the options under the "Advanced Conditions" as in the following picture:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=82042&stc=1&d=1219101036[/IMG]
Note that to get the last line you need to click on the plus button.  This will give you a line with a checkbox that says "new-scheme" and "New Scheme Description".  Click on "new-scheme" and change it to "trash" (this must be "trash") and click on "New Scheme Description" and put in the description.

That is it.  Now if you right click on an item in the trash you will see an option called "Undelete."  Select that and follow the prompts (if any).  If you try to undelete a file and a new file exists with the same name where the file originally was, then you will be asked what to do.  Otherwise the file will be quietly restored to its original location.

**Caveat:**  This script can only undelete entire directories (and everything in them) that were deleted.  It can not undelete files or directories inside of a deleted directory separately from the parent directory.

**Fix to Caveat:**  I have updated the script to fix the above caveat.  Note the change in the parameters in the "Menu Item & Actions" tab of the nautilus configuration.

**Fix:**  The script has now been updated and can recover files deleted from other file systems.  

Please let me know if any bugs are encoutered.

To **undo** what has been done, run the following commands:
```
rm ~/bin/undelete-trash
sudo apt-get autoremove gvfs-bin nautilus-actions
```
Note:  If "zenity" was actually installed at the beginning, you may want to remove that as well.  However, I believe that zenity is installed in a default installation of Hardy, so I did not include it in the uninstall command above.

---

### Post by anthropoidster on 2008-08-22
Wonderful! Works great! Thanks

---

### Post by kostaslinux on 2008-08-27
it doesn't work for every file on my computer. It works for files and folders that were on desktop but not for these that are in a external disc or Home folder

---

### Post by glennric on 2008-08-28
> **kostaslinux said:**
> it doesn't work for every file on my computer. It works for files and folders that were on desktop but not for these that are in a external disc or Home folder

This should work for anything that is in your users home directory.  As to files on an external disc or another file system, give me a little bit of time and I can make the script work for those too.

---

### Post by Hire on 2008-08-28
Useful, works great thanks :D

---

### Post by glennric on 2008-08-28
> **kostaslinux said:**
> it doesn't work for every file on my computer. It works for files and folders that were on desktop but not for these that are in a external disc or Home folder

I have updated the script so that it works for files deleted from other file systems.  It should now be able to recover anything that you have permissions for.

---

### Post by RequinB4 on 2008-08-29
FYI, this should be a default feature in the new version of nautilus coming in Intrepid Ibex.

---

### Post by glennric on 2008-08-29
> **RequinB4 said:**
> FYI, this should be a default feature in the new version of nautilus coming in Intrepid Ibex.

That is what I said in the first paragraph of this tutorial.

---

### Post by exploder on 2008-08-29
glennric, thanks for the "How To"! This is a very nice feature to have!

---

### Post by malspa on 2008-08-29
It seems that you can also simply drag an item from the trash (from the file browser) back to the desktop or back into another directory.

---

### Post by glennric on 2008-09-01
> **malspa said:**
> It seems that you can also simply drag an item from the trash (from the file browser) back to the desktop or back into another directory.

Of course you can.  The point is to have a right click option that will restore files from the trash to its original location before it was deleted.  Just like in windows.  This is what the gnome developers have planned.  It just isn't fully implemented yet.

---

### Post by malspa on 2008-09-02
> **glennric said:**
> Of course you can.  The point is to have a right click option that will restore files from the trash to its original location before it was deleted.  Just like in windows.  This is what the gnome developers have planned.  It just isn't fully implemented yet.

Yeah, I understand the point, thanks.  I did read the title of the thread.  I just threw that post in there because lacking the right-click option, it's still a simple matter to drag an item back to its original location from the trash, for anyone who doesn't want to go through the steps that you presented here.  Good job, by the way!

---

### Post by glennric on 2008-09-02
> **malspa said:**
> Yeah, I understand the point, thanks.  I did read the title of the thread.  I just threw that post in there because lacking the right-click option, it's still a simple matter to drag an item back to its original location from the trash, for anyone who doesn't want to go through the steps that you presented here.  Good job, by the way!

Yeah, that is a good point.  I am going to add a comment about that in the tutorial.

---

### Post by me22 on 2008-11-03
Thanks, this was very helpful.  (Accidentally deleted some music folders, and this way I get the fordering back easily.)

For people that would like a cruder way, but that requires less setup:

1) Install gvfs-bin

sudo apt-get install gvfs-bin

2)Save this as "undelete-all.pl".

```

#!/usr/bin/perl

$trashpath = "trash:///";
$lsprog = "gvfs-ls";
$infoprog = "gvfs-info";
$mvprog = "gvfs-move";

@allfiles = split("\n", `$lsprog $trashpath`);

foreach $file (@allfiles) {
    $file = $trashpath . $file;
    
    $origpath = "";
    for (split("\n", `$infoprog "$file"`)) {
        if (m{trash::orig-path: (.+)$}) {
            $origpath = $1;
            last;
        }
    }
    unless ($origpath) {
        print STDERR "Unable to find origpath for `$file'!\n";
        next;
    }
    print "Do you want to restore `$file' to `$origpath`? [y/N] ";
    if (<STDIN> eq "y\n") {
        print "Working...";
        $failed = system($mvprog, "--interactive", #"--progress",
                         $file, $origpath);
        if ($failed) {
            print STDERR "Error moving `$file' to `$origpath'!\n";
        } else {
            print "Success\n";
        }
    } else {
        print "Skipped.\n";
    }
}

```

3) Open a terminal, and run

perl undelete-all.pl

4) Answer the questions.  Anything other than y will skip the file.

---

### Post by glennric on 2008-11-09
I want to point out that this tutorial is now obsolete with the release of Intrepid Ubuntu 8.10 as this feature is now standard in Gnome.

---

### Post by exploder on 2008-11-09
> I want to point out that this tutorial is now obsolete with the release of Intrepid Ubuntu 8.10 as this feature is now standard in Gnome. 

Not necessarily, many will stay with Hardy because of it's LTS status. I have referred back to this thread when setting up Ubuntu and LinuxMint for others. This is a very nice addition for people new to Linux.

---

### Post by glennric on 2008-11-10
Good point Explorer.

---

