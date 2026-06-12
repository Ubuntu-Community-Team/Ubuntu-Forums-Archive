---
title: "Understanding the &quot;File Browser&quot;"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-26
One of the critical applications on a windows PC is the "Windows Explorer" and I've been trying to figure out the equivalent in ubuntu.

Four ubuntu applications seem to be related - file browser, terminal df -H command, disk utility and disk analyzer.

(1)file browser, which seems to be called "home folder" in unity and perhaps "places" in classic, but I can't see the application in the "applications" tool, so I'll call the file browser "home folder" because that is the name that shows up in the global menu when the file browser has focus (seems strange)   

The column for size does not give the file size like the other applications, but instead lists the number of files in the folder.  The size of the folder, in bytes does not seem to be available.  Is there an option to also display the size in bytes of the folders?

What is the best term to refer to the file browser? (can't see the term file browser used anywhere)

(2) terminal command df -H gives columns for Filesystem, Size, Used, Avail, Use% and Mounted on with the columns displaying what we expect.

(3) disk utility - gives useful basic information about drives, the term capacity is used instead of file size and also lists a place for Available, but the available space information is not provided.

(4) disk usage analyzer - lists folder, usage graph and %, size (bytes as expected), and contents (number of items)

= = = = 
At the moment I'm focused on the home folder application (file browser), where we seem to be able to get down to the level of looking at individuaL files.  Not sure if in linux if file extensions are used or not - don't see extensions in the file names, but windows (strangely) hides extensions by default - not sure about Linux.

In the "home folder" (is this really the name of the application (file browser), I clicked on the close left pane button.  I expected (hoped) there  would bea button to display left pane, but have found none so far or a reference in searches I've done.   

Anyone know how to display the left pane in the file browser, if closed, short of reinstalling?

Are there conceptual mistakes or omissions in the 4 ubuntu tools above which do the functions (and more) of the Windows Explorer tool?

Thanks! - studying ubuntu.

---

### Post by zeroseven0183 on 2011-09-27
I think what you are referring to is Nautilus. It is the [default file manager of Ubuntu]("https://help.ubuntu.com/community/DefaultFileManager"). If you could clarify which version of Ubuntu/Linux you are using? Please.

By default, Nautilus displays the extension of files and the date it was last modified.
To display the left pane in Nautilus, click View and check Side Pane.

---

### Post by Denver Dave on 2011-09-27
Nautilus - thanks.  Part of my confusion is that this application name is not listed when searching applications, nor does the name appear on any of the title bars.  But maybe this is because Nautilus is a basic function like applications?

Thanks - I'm struggling a little, but I think if I can get comfortable with the file system tools, it will go a long way in getting me comfortable with ubuntu.

= = = = = 

Sorry - good point.  I'm running the unity menu with ubuntu 11.04.  

Still haven't figured out how to re-open the left panel, but now with Nautilus in my searches, I'm finding more info.  Will also try link provided.  Also, "file manager" is probably a better term for me to use than "file browser" which is the term that is used on page 90 of "The Official ubuntu book" which I consulted while trying to locate a way to re-open the left panel.

---

### Post by dFlyer on 2011-09-27
1. The default file browser in Gnome is Nautilus, (not home folder even though home folder opens Nautilus) if you look under preferences you can change settings. File extensions are not required for linux and are optional only. You can click on a file in Nautilus and get the file size displayed on the bottom of the Nautilus bar. You can also click where it say icon view and change it to list view which will provide more file information.

"Are there conceptual mistakes or omissions in the 4 ubuntu tools above which do the functions (and more) of the Windows Explorer tool?" --Not sure what your referring to here. I haven't used windows in so long I'd be afraid to guess.

As far as the left side panel goes press F9 or under view click side panel.

My advice is to explore more before you ask questions.

---

### Post by Denver Dave on 2011-09-27
> **dFlyer said:**
> 
As far as the left side panel goes press F9 or under view click side panel.

My advice is to explore more before you ask questions.

Thank you, thank you.  F9 did display the left panel.

I did search for at least a half hour before posting this message and was unable to find the F9 solution for opening the left panel.  Of course I was handicapped by not knowing the name of the application (file manager / Nautilus) that I was trying to research.

Now that I know that Nautilus is the name for the "file manager" I did find the following, which will hopefully help me and others:  I do still find it somewhat strange that there is a close side panel button, but no displlay side panel button, but I know how to do it now - thanks. 

= = = = = =
Later note - while evaluating why I could not find the answer on my own.   The global menu fooled me and I did not relate it to the Nautilus application.  If I had, I would have looked under help and also edit preferences for some way to display the left panel.  I should have done that, but if I had, at the moment, I don't see the short-cuts or information about re-opening the left panel given.  Might be there, its late, but don't see it.  However, help and about, would have given the term Nautilus and a link to the Nautilus website - don't see the shortcuts there either, but I assume there someplace.
= = = = = = =

However, once the name of the application "Nautilus" is known, with internet searches we can find:

Nautilus Shortcuts

You might want to remember some these combinations like the one to create new folder or rename a file.

    Shift + Ctrl + N &#8211; Create New Folder
    Super + T - Opens the Trash can (recycle bin)
    Alt + Home &#8211; Opens Home
    Ctrl + T &#8211; Delete selected file(s) to trash
    Alt + ENTER &#8211; Show File/Folder Properties
    Ctrl + 1 &#8211; Toggle View As Icons
    Ctrl + 2 &#8211; Toggle View As List
    Shift + Right &#8211; Open Directory (Only in List View)
    Shift + Left &#8211; Close Directory (Only in List View)&#65279;
    Ctrl + S &#8211; Select Pattern
    F2 &#8211; Rename File
    Ctrl + A &#8211; Select all files and folders
    Ctrl + W &#8211; Close Window
    Ctrl + Shift + W &#8211; Close All Nautilus Windows
    Ctrl + R &#8211; Reload Nautilus Window
    Alt + Up &#8211; Open parent directory
    Alt + Left &#8211; Back
    Alt + Right &#8211; Forward
    Alt + Home &#8211; go to Home folder
    Ctrl + L &#8211; go to location bar
    [COLOR="Red"]**F9 &#8211; Show sidepane**[/COLOR]
    Ctrl + H &#8211; Show Hidden Files
    Ctrl + + &#8211; Zoom In
    Ctrl + - &#8211; Zoom Out
    Ctrl + 0 &#8211; Normal Size

---

### Post by vasa1 on 2011-09-27
> **Denver Dave said:**
> ... I was handicapped by not knowing the name of the application (file manager / Nautilus) that I was trying to research.

Now that I know that Nautilus is the name for the "file manager"...

Hi Dave! Yes, it is a bit confusing. I too was thrown off for a while till I realized that Text Editor = gedit and PDF Viewer = Evince (unless you change the defaults, which I haven't done). The use of both generic titles and program names is one of the wee hurdles we newbies have to deal with :D

---

