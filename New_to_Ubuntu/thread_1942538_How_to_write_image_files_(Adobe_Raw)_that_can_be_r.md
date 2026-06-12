---
title: "How to write image files (Adobe Raw) that can be read on a Mac"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-17
Dear Ubunters: I used Brasero to burn a CD of Adobe Raw images (NEF files). The files can be opened on Ubuntu machine (11.04) but not on my Mac (OS 10.4). How can I burn files that can be read on both systems? 

My current workaround involves opening (on the Ubuntu machine) the files in Fspot, then saving them as ppm files (Fspot doesn't open a dialogue box that offers any other file extension, so I'm stuck with using only ppm as an extension). 

I then open the files in GIMP (where I've installed DCRaw) and save them as PSDs or TIFFS, Jpegs, etc. Only then can I read them on my Mac. 

One more problem: GIMP automatically resizes the images to something like 160 x 220 pixels, even though the files being opened are (on average) 14.5 megs. I've looked through Edit Preferences in GIMP and haven't seen any options for stopping the auto discard of pixels. Arrrrrgh! 

I'd appreciate help with these two problems: 

1: Burning a Mac-readable disk on an Ubuntu machine); 

2: Help importing RAW files without downsizing them would be much appreciated (regarding the latter problem, it's not just a thumbnail that's being presented as the downsized image; I attempted to print the image, and sure enough, it's 0.5 x 0.4 inches, down from the original, which is something like 17 inches on its longest dimension). 

Please note: I've also tried UFRaw, which doesn't stop the downsizing from happening in GIMP.

Many thanks, 
Joel

---

### Post by jwbrase on 2012-03-17
> **jps2012 said:**
> Dear Ubunters: I used Brasero to burn a CD of Adobe Raw images (NEF files). The files can be opened on Ubuntu machine (11.04) but not on my Mac (OS 10.4). How can I burn files that can be read on both systems?


> 1: Burning a Mac-readable disk on an Ubuntu machine);

Is it the files you can't read, or the disk itself? 

If you can browse the disk, but can't read any of the files on it, then you just need to find a program that's available for OS X that will read Adobe Raw files. I don't have a Mac or do much with Adobe Raw files, so I can't give you much advice there.

If your Mac can't read the disk itself, then it's likely a hardware problem involving either your CD burner or the CD drive on the Mac. (There's also the chance that it could be an issue with Brasero).

---

### Post by mcduck on 2012-03-17
Do you actually have any program installed on the Mac for reading .NEF images? Any disc you burn on Ubuntu will be readable on a Mac, so it's just a question of having support for Nikon's RAW files on the Mac system.

What comes to Gimp resizing images,no, it doesn't do that, and neither does UFRaw. It sounds like you are doing something wrong in your RAW image workflow, and are using the JPEG thumbnails your camera saves in the .NEF file instead of the actual RAW image.

Could you tell in more detail what exactly are you doing now to open the .NEF file on your Ubuntu system? The size you described would pretty much fit the embedded thumbnail size, and while I haven't used Fspot for ages, the last time I've used it it didn't read anything else than the thumbnail from .NEF files. You really should use a RAW editor with RAW files (not that there would be much reason to shoot in RAW format anyway if you don't use a RAW editor ;))

---

### Post by jps2012 on 2012-03-18
Thanks for the replies, MC and JW. I'd asked about the issue of "CDs" not being able to be read on a Mac after being written on an Ubuntu system. It's the image files (Adobe Camera Raw, as NEF files) that can't be read (my apologies for not being clearer). 

Yes, I've tried to open them on a Mac (OS 10.4) in Photoshop, which does read RAW files--if those files are downloaded and written to a CD on a Mac. It's going cross platform that seems to cause the problem (which might not really be a platform issue, so much as it might be an issue with Brasero). 

I've been using RAW for about three years, and haven't had a problem (other than the occasional issue with an individual file) when I've downloaded from CompactFlash cards directly to a Mac. But I started using Ubuntu about a week ago and ran into this hurdle, with files not opening when I cross platforms. 

MC, you asked "Could you tell in more detail what exactly are you doing now to open the  .NEF file on your Ubuntu system?" 

I've tried several ways of opening the files on my Ubuntu system (which isn't really the problem; it's opening them on a Mac that's the issue). The only way I've been able to open them without GIMP automatically downsizing them is to open them in UFW, then save them as PPM files. If I try to open them as Raw files (NEF extension), GIMP automatically downsizes them (see below). 

Regarding the possibility that I'm opening the JPG files instead of the RAW files: that's a good guess, but no, that's not it. The files appear as RAW files on my system, not as JPGs. The file sizes (when I view them in a Finder window on a Mac or a Places window on Ubuntu) are the same size (an average of 14.5 megs per file, which is the largest file my Nikon D300 will make, which is a RAW file--the kind I've been using for the last three years). 

If I open them on a Mac (having first imported them from CompactFlash to a Mac) they open as RAW files (confirmed as such by being opened in a unique editing window in Photoshop). If I open them on an Ubuntu system using UFRaw, they open as RAW files, not as JPGs. 

I really, really wish I could show you a screenshot of how the files post (meaning 'appear') in UFRaw, versus GIMP. In UFW they appear (with an automated 'message' indicating the pixel dimensions) as 4320 x 2868 pixels (which is what they also appear as in Photoshop). 

In GIMP, the same file opens with an automated 'message' saying that the file is 160 x 120 pixels. A print (as on paper) confirms that GIMP is automatically downsizing the image; the image is heavily pixelated--useless other than for web use. In other words, the 160 x 120 isn't a measure of a thumbnmail--it's a measure of the now extremely downsized original image, with roughly 29 of every 30 pixels in the original having been discarded.

I know that's a horrific amount of detail. I'm posting it because I'd really like to be able to move over to open source programs (and circumvent being chained to Adobe, Word, etc.), and learn how to problem solve in Linux. I appreciate the time it takes you all to read this, decode it (!) and reply. 

Joel

---

### Post by mcduck on 2012-03-18
> **jps2012 said:**
> 
I've tried several ways of opening the files on my Ubuntu system (which isn't really the problem; it's opening them on a Mac that's the issue). The only way I've been able to open them without GIMP automatically downsizing them is to open them in UFW, then save them as PPM files. If I try to open them as Raw files (NEF extension), GIMP automatically downsizes them (see below). 

Do you have te Gimp plugin for UFRaw installed? What happens if you open the file in UFraw, adjust the colors etc as you like, and then click the "Open in GIMP"-button instead of saving the file as PPM? (besides, UFRaw sure supports more up-to-date formats than PPM. If you really must save the file in between, I'd suggest using PNG or TIFF format. Both allow lossless compression and are more widely supported these days...)

> **jps2012 said:**
> 
Regarding the possibility that I'm opening the JPG files instead of the RAW files: that's a good guess, but no, that's not it. The files appear as RAW files on my system, not as JPGs. The file sizes (when I view them in a Finder window on a Mac or a Places window on Ubuntu) are the same size (an average of 14.5 megs per file, which is the largest file my Nikon D300 will make, which is a RAW file--the kind I've been using for the last three years). 
I'm not talking about opening a JPEG fiile, I'm talking about opening a thumbnail image encoded in JPEG format, embedded inside the .NEF file (which is what Nikon cameras do). If the program you try to open the image with doesn't have proper support for NEF format, they might end only opening the embedded thumbnail instead of the actual RAW data. Using UFRaw plugin with GIMP should solve that problem.

> **jps2012 said:**
> 
If I open them on a Mac (having first imported them from CompactFlash to a Mac) they open as RAW files (confirmed as such by being opened in a unique editing window in Photoshop). If I open them on an Ubuntu system using UFRaw, they open as RAW files, not as JPGs. 


> **jps2012 said:**
> 
I really, really wish I could show you a screenshot of how the files post (meaning 'appear') in UFRaw, versus GIMP. In UFW they appear (with an automated 'message' indicating the pixel dimensions) as 4320 x 2868 pixels (which is what they also appear as in Photoshop). 

In GIMP, the same file opens with an automated 'message' saying that the file is 160 x 120 pixels. A print (as on paper) confirms that GIMP is automatically downsizing the image; the image is heavily pixelated--useless other than for web use. In other words, the 160 x 120 isn't a measure of a thumbnmail--it's a measure of the now extremely downsized original image, with roughly 29 of every 30 pixels in the original having been discarded.
This would, once again, suggest that you are seeing the embedded thumbnail, not the actual RAW data. GIMP doesn't downsize the image, the thumbnail is all it sees because the way you are opening/converting the images isn't correct.

So, my suggestion is to try this: First, make sure you have the [gimp-ufraw]("apt:gimp-ufraw") package installed. Then open the image in UFRaw, adjust as you want, and finally press Alt-G (or click the GIMP icon in bottom right screen corner) to send the image to GIMP.

...and if you need to save images directly from UFRaw, the save format options are on the second to last tab. THe file format is selected from the dropdown menu right next to file name.

---

### Post by jps2012 on 2012-03-25
MCDUCK: I think you're right. I think I don't really have the UFW plugin installed in GIMP. I'm trying to figure out how to do that. I found some recommended commands, and this is what I tried to do (but failed to get it to complete). 

Here are the instructions I'm trying to follow (I'm stuck at the part where I'm supposed to cd to the new folder the UFRaw tarfile created--I'm wondering how I can find the name of the most recent folder created on my system--if such a command exists in bash):

---

### Post by jps2012 on 2012-03-25
This is SORT OF good news: I found the new directory for UFRaw, and was able to switch to it. I ran the command "./configure" and got the following response from bash: 

"configure: error: Package requirements (glib-2.0 >= 2.12 gthread-2.0) were not met:

No package 'glib-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix." 

Does this mean I need to install more packages/software before I can configure the UFRaw plugin? Again, my goal is to get the UFRaw plugin into GIMP.

---

### Post by mcduck on 2012-03-25
> **jps2012 said:**
> MCDUCK: I think you're right. I think I don't really have the UFW plugin installed in GIMP. I'm trying to figure out how to do that. I found some recommended commands, and this is what I tried to do (but failed to get it to complete). 

Here are the instructions I'm trying to follow (I'm stuck at the part where I'm supposed to cd to the new folder the UFRaw tarfile created--I'm wondering how I can find the name of the most recent folder created on my system--if such a command exists in bash):

Just install the plugin from Ubuntu's repositories. Works perfectly, I'm using it all the time for .NEF files from my Nikon DSLR. :D

So all you need to do is click the link in my previous post, or use Ubuntu Software Center/Synaptic/apt-get/whichever package manager you prefer to download & install it.

(the error messages you got while trying to manually compile the plugin were telling you that you haven't got the development libraries for glib-2.0 and gthread-2.0 installed. But there really should be no reason to compile the plugin yourself.)

---

### Post by jps2012 on 2012-03-25
MCDUCK: Several days ago I downloaded the plugin from the link you provided, but it didn't uncompress or otherwise install within GIMP (which is why I'm trying to do it command by command). 

I also tried downloading it via the Software Center. That download allowed UFRaw to be installed as an independent program--not a GIMP plugin. 

I was just looking at my bin folder, and noted that "make" "configure" and "install" are not listed as bash commands there. Given how ignorant I am about scripting, I don't know if that's what's causing me from being unable to invoke "configure," but it seems reasonable to assume so. 

Is there a development package I could link to that pull in those commands? And wouldn't cause a Catch-22 (where I would need to configure the configure command before using the configure command ... ?

---

### Post by jps2012 on 2012-03-25
Problem solved! (Well, ONE of the problems.) MCDUCK, I went to the Ubuntu Software Center and started searching for GIMP plugins. Here's where I went wrong: I assumed downloading UFRaw would install the needed plugin in GIMP (foolish!). 

It has to be downloaded from the file "gimp importer for raw camera images." Please note (others who are struggling to open RAW images), the plugin doesn't have "UFRaw" as part of its name. 

Now I can export Raw files from UFRaw into GIMP. In Photoshop CS3 they open as 15 meg files. In GIMP they're 118 megs. Ouch! 

I still don't understand why I don't have configure, make and install commands listed in my bin folder (for scripting in bash). If anyone could address that--and note whether that's likely the cause of the errors listed below--I'd appreciate it. 

Thanks for sticking with me, MC.

---

### Post by mcduck on 2012-03-25
> **jps2012 said:**
> Problem solved! (Well, ONE of the problems.) MCDUCK, I went to the Ubuntu Software Center and started searching for GIMP plugins. Here's where I went wrong: I assumed downloading UFRaw would install the needed plugin in GIMP (foolish!). 

It has to be downloaded from the file "gimp importer for raw camera images." Please note (others who are struggling to open RAW images), the plugin doesn't have "UFRaw" as part of its name. 

Now I can export Raw files from UFRaw into GIMP. In Photoshop CS3 they open as 15 meg files. In GIMP they're 118 megs. Ouch! 

I still don't understand why I don't have configure, make and install commands listed in my bin folder (for scripting in bash). If anyone could address that--and note whether that's likely the cause of the errors listed below--I'd appreciate it. 

Thanks for sticking with me, MC.

UFraw sure is included in the name of the package ("gimp-ufraw"), just not in the description which is what you'll see if you install the package from the UFRaw's "page" in Software Center .Seeing the plugin package on it's own would require you to specifically search by it's exact name, or search for "ufraw" and then click the "show 2 technical items"-option at the bottom left corner of Software Center.

What comes to the problems you had when trying to compile the package yourself, the errors you posted here are explained by not having the development libraries for the mentioned packages, like I said in my previous post. *configure* si not a program, it's a script that comes with the source code, so you aren't even supposed to have it in your system binary directories. "make" is located in /usr/bin, and "install" isn't a command of it's own, it's an option for the "make" program. And none of these is needed for Bash scripting, they are all strictly related to compiling programs. Anyway, you should always check if a program is available through the package management before using any other way to download it...

---

