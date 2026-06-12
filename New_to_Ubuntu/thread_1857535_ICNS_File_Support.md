---
title: "ICNS File Support"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by nair on 2011-10-10
For those who are not familiar with the .icns file type, it is a specific image format known as the "Apple Icon Image Format".  It is specifically designed for making icon images which are used on Mac OS X to represent Mac applications, as well as Mac directories.  I was curious if it would be possible for any Linux-based operating system to add native support for viewing, editing, and creating .icns files.

  Perhaps some or all major Linux distributions already support them, but in my brief experience using Ubuntu, native support for .icns files does not exist&#8212;using the latest, freshly updated 11.04 64-bit version.  Let me first provide some information about what tools are already available for Linux, and then I will describe for what exactly I am seeking.

  I was able to use Ubuntu to download and install the &#8220;libicns&#8221; utility, which is available through the Ubuntu Software Center, among other places, and I was able to use the utility to convert a .png image to an .icns image.  I tested this .icns image on Mac OS X, not only by simply viewing the image by using the Mac &#8220;Preview&#8221; application, but also by compiling a Mac application in C++, embedding the .icns image in the application as its icon, and testing the icon visibility in different scenarios.  In every scenario I arranged, I was able to view the application both in the dock and in the &#8220;Finder&#8221; application and see the correct .icns icon image displayed.

  &#8220;libicns&#8221; is an open-source utility, licensed under the LGPL.  It is a fairly straight-forward, small, terminal-based utility which is very accessible and functional for Linux users, judging by my brief experience with it.  It would seem to me that the utility itself, or something very comparable, could be thrown into a Linux distribution as an out-of-the-box operating system feature.  This would at least give the user the ability to convert .png files to .icns files, and vice versa.  Ultimately, though, if an Ubuntu user has to deal with .icns files, the ideal solution for them would be to have the ability to:

[LIST]
[*]View the .icns image in a standalone application, where they can interact with the image itself, although perhaps not edit it.  Editing would be more of an advanced task, reserved for the more specialized software like GIMP (which, notably, I was not able to use to manipulate .icns files, although I spent very little time attempting to do so).
[*]View the .icns image thumbnail in a directory.
[*]Create an .icns image by converting from some other image of a more generic file type, such as .png.  This would have to be done by either allowing the renaming of the file to make that change (performed in a directory or desktop interface of the operating system, meaning the operating system would have to arrange for that conversion to take place behind the scenes), or by opening the file in some sort of native image viewer and then performing a &#8220;Save As&#8221;, making sure to change the file type to .icns.
[/LIST]

Obviously, .icns files are certainly not Linux-inspired file formats&#8212;quite the contrary&#8212;and therefore having a Linux distribution like Ubuntu capable of handling .icns files in some or all of the ways I have mentioned above may not seem particularly reasonable or desirable.  However, in my experience, it has been Linux above all other operating systems which has been able to at least &#8220;handle&#8221;, in some way, basically any type of data.  Whether that be by interacting with an obscure, proprietary file format or reading from or reformatting a disk with some platform-specific file system like NTFS, Linux is traditionally very capable in this domain&#8212;which leads me to my question:

  Let us assume that GIMP is still included as part of a default installation of Ubuntu, and let us assume that GIMP is able to affectively create and edit every type of image format, including that of .icns.  This affectively takes the issue of editing .icns images off of the table.  If this were the case, which is essentially an ideal scenario for the purposes of this discussion, then how would it be possible for the operating system to do the other things I described, like properly view any and all .icns image thumbnails in directories, or convert an image of a generic type to an .icns type&#8212;using either a file renaming method (modifying the extension using the operating system) or the &#8220;Save As&#8221; method built into the native image viewer (using a basic image application expected to be part of the standard set of applications built into the operating system)?

  I am a novice Linux user as well as a novice programmer, and my research in this area is very limited at this point, as I have just begun.  It is entirely possible that I am asking for something that is extremely difficult to provide or that I have otherwise &#8220;missed the boat&#8221; on some major issue relevant to this discussion.  It also might be an area of Linux development which simply does not have a lot of user demand for new advancements.  While they may be true for .icns files specifically, I do not believe that will be true across the board for all types of somewhat obscure file types, file systems, and so forth.  Therefore, this discussion is still relevant outside of the specific context of .icns files, although that is the specific file type over which I am currently fixated.  If you have any suggestions regarding new tools to try, additional libraries to download, ideas for potential development efforts, or general comments regarding this topic, I welcome your response.

---

