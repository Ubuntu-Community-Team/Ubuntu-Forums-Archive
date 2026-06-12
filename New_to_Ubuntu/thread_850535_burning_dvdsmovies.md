---
title: "burning dvds/movies"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-07-05
i just downloaded zeitgeist the movie and i want to burn it to a dvd but on brasero you can only burn data dvds and iso images so how should i do this?

---

### Post by Teber on 2008-07-05
if it is an avi or mpeg or something, try devede. it can be found and installed through applications/add/remove.

---

### Post by Return Privacy on 2008-07-30
Hello,
I also have mpeg 2 video files (recorded TV shows) that I want to burn to DVDs that will play on a set top player. I looked for DeVedee all over the web and can't find it anywhere? Do you know if it is still available? I also read on here that there is a program named Torvid, that will burn video files to movie type DVDs, do you have any suggestions?
I am using Ubuntu 8 desktop. It is the first linux OS I have ever used. So far I love it. I figured out how to use Brasero to burn data CDs, but that program won't burn movie type DVDs. 
:confused:

---

### Post by hyper_ch on 2008-07-30
try K3B or DeVeDe (both are in the repos)

---

### Post by Teber on 2008-07-30
yes, the repos. that's where i found devede.

---

### Post by Brandel Valico on 2008-07-30
My own suggestion is ManDVD 

[http://www.getdeb.net/search.php?keywords=mandvd](http://www.getdeb.net/search.php?keywords=mandvd)

it's very similar to what alot of people coming from Windows are use to. It's a very simple and clear GUI method with Menu building in the program. 

The getdeb site is a useful site to bookmark.

You may also want to look into K9Copy it's is useful for backing up your owned DVD's and they are starting to add a DVD creator into it also.

---

### Post by Return Privacy on 2008-07-30
Thanks Hyper, Brandel, and Teber

I found DeVeDe on getdeb site you listed. I haven't tried to download it yet. I am new and haven't installed a program on Ubuntu yet. I had someone else put Ubuntu on the machine for me. I want to learn as much as I can, so I don't have to have someone else do everything. Do you know if I can download DeVeDe on my mac, put it on a usb thumb drive and install it from that on Ubuntu machine? Or do I have to download it from the UBuntu machine? I really want to get this set up and working by myself (with your help on here) so I don't have to have the local guy do it for me. 
Thanks guys

---

### Post by ReturnPrivacy on 2008-07-31
Hi again guys,
I installed Devede, and put two mpeg2 files in it. It converted them, but it made one xml file, and one title mpeg2 file, and one video mpeg2 file? How do I burn that to a DVD? I set it to make an ISO that I could burn to DVD, but it didn't do that? I tried it again, and checked the box that said "this file is already in mpeg 2 dvd format". This time it created a video_ts file and an audio_ts file, that's it. How would I burn that to a DVD in Ubuntu? I really wish I could just get it to burn the ISO file like it is supposed to do, then I could use Brasero to burn it to DVD?

---

### Post by Brandel Valico on 2008-08-01
Well if the Video TS and Audio TS files are working. (Try Going into the Video TS Folder and open one of the files you have there and see if it plays.)

You could use K3B (Which you can install by typing "sudo apt-get install K3b" Into a terminal It will of course ask for your password.

You also could probably find it for download in Synaptic or on the Get Deb site also if you more comfortable with the goto a site to download it method

Oh and for the whole downloading of a program on different computers. It can be done as long as you for now make sure the program your downloading ends with a ".deb" for now anyway. Once your used to it you can download pretty much any Linux based file and just convert it over to work on a Debian based machine.

---

### Post by Return Privacy on 2008-08-01
Hi 
I used Devede and had it set to "create an .iso/cun bin". It did create the .iso file from the two mpeg 2 video files. I right clicked on the .iso file and clicked on "burn to disc". It said the DVD would be 3.5 gb in size. It burned fine. I put that DVD in a set top, and it won't play. I put that DVD in the Ubuntu machine, a mac, and an xp machine. THe DVD shows up in all three the same way, it just says "DVD-Video", and it says it is 3.5gb, but it shows no files at all? It says it is UDF format. I can't get the DVD to do anything. I tried this twice, and got the same results. The only other options in devede are to "create disc structure" and "only convert to mpeg compliant files". It only allows you to choose one, so I choose "create an iso cun/bin"
I'm lost, any help would be greatly appreciated?????
Just to remind you, I have regular mpeg2 recorded video files to burn to DVD to play on set top.
Thanks:confused:

---

### Post by Return Privacy on 2008-08-03
Brandel,
I installed k3b, and tried to burn just the video_ts and audio_ts files like you said, but k3b won't burn them. It says there is an error in the video_ts file? I tried with a new mpeg2 file that was written by devede to just the compliant mpeg2 files, and it did the same thing, error?

I must be missing something here? These are just plain old mpeg2 video files, nothing fancy. I just want to burn them onto a DVD that will play on a set top?

Right now, I am trying to burn the iso file that I just had devede creat:confused: from the mpeg 2 files. I am trying to burn it with k3b this time. I'll let you know if that works or not.

---

### Post by Return Privacy on 2008-08-03
Well,
This is not working at all. I just took an iso that devede created from mpeg 2 video files. I burned it to DVD with k3b. It says it is a "DVD-Video" disc on the computer, and says it has 3.46gb used, but there is nothing there. It won't play on the computer or on a set top box.

I think the problem lies with devede program. For some reason it is not making a correct iso file out of the mpeg 2 files. Even if I just have it burn to compliant mpeg files, video_ts and audio_ts, and burn them, the dvd won't play. 
I'm guessing that devede program has a problem.

HELP!:mad:

---

### Post by Brandel Valico on 2008-08-04
It does seem to not be working very well.

I don't really use DeVeDe at all myself.

Sorry I can't be of more help. The only think I can think of is that for some reason it's not accepting the video files you have as dvd compliant video's you may need to re-encode them. Then try and create and Iso. file with them.

---

### Post by Return Privacy on 2008-08-04
Hi Brandel,
I couldn't get devede to work right. I installed tovid, now called todisc. When I put an mpeg2 file in it, and told it to create the iso, it started and stopped in about a 1/2 of a second, but produced nothing at all? I don't think I installed tovid correctly or something? 
I finally installed ManDvd. I downloaded it from a deb site link. (I'm new at linux, so don't know what deb means). It said it installed correctly, and has all the necessary "dependencies", whatever that means? I just put two mpeg2 files in it, and it is encoding them now. I hope it will create and burn a proper DVD that I can play on a set top player......I'll let you know what happens.

---

### Post by Return Privacy on 2008-08-05
Finally!
I used ManDvd. I put two mpeg2 video files in it, and told it to create a DVD. I left all the settings at default, and only used the file names in the menu. It transcoded the whole thing and then asked me if I wanted to use K3B to burn the DVD. I said yes, and then it burned the DVD. It's weird that the DVD won't play on the computer, but it WILL play on the set top DVD player on the TV. That's fine with me. 
This has been a long journey to simply burn mpeg2 video files to a playable DVD. Tovid(todisc), DeVede, and others would not work at all. 

My only question is this. Why doesn't Ubuntu make it easier to install a program? What are dependacies, repos, debs, libxxs, multiverse, universe, etc, and all that stuff mean? This is the kind of thing that most users hesitate at when trying Linux. Ubuntu is my first attempt at learning Linux. I'm more determined than most people, and don't like to give up. IMHO Ubuntu should make ALL programs complete with everything necessary to make them work when they are installed. (or at least, the main program should install and then prompt you to install what it needs, with links to them) end of my rant..:^):KS

---

### Post by Brandel Valico on 2008-08-06
Burning video to playable DVD is one of the harder things to get going in Linux in my opinion that and game playing are the only weak areas in an otherwise wonderful OS. As for why it doesn't give you everything you need in each program. My understanding of it is this. Linux only installs each dependency one time and then every program that uses them uses the same one. Where as in windows when you install a program you do get everything you need in each program. But when you install other programs that may use the exact same dependency it will install it yet again and again and again for each and every program that needs it slowly using up disk space.

Where as Linux just does it once and that one time is used by all programs.

(Thats my understanding of it. It may not be right though I'm still learning also.)

A .deb file is basically like an .exe file in windows. It's the installable file. For the program.

Repo's are a wonderful thing. Think of them as a large collection of programs you can download from. Medibunutu for example is a wonderful resource for getting DVD playability working.

Which may be why the dvd disc won't play. By defualt Linux doesn't come with DVD playing capiabilty due to licensing issues. 

The very well written walkthrough found here will get you all the Multimedia things you need to do so.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

It's the first thing I do when I do a fresh install of Ubuntu.

There is a learning curve to be sure when switching to Linux but it's well worth the effort in the long run. Stick with it. You won't regret it.

---

### Post by Brandel Valico on 2008-08-06
Also glad to see you get it working to at least burn DVD's. Mandvd is probably the best current dvd creator in Linux. A few other programs you will probably want are K9copy if you don't have it yet. It functions like dvdshrink or clonedvd from windows. Allowing you to make duplicates of your dvd's and even shrinking dual layer to fit single layer dvd's then burning them in K3B. Also if you want to play alot of the games or still run certian windows programs you will want "Wine".

---

### Post by halitech on 2008-08-06
I've used Devedee and manDVD for what seems like forever. The only trick I've found with Devede is to not burn from within the program. Have it create the iso file and then exit the program and then use K3B to burn it. I'm not sure about Brasaro but I'm wondering if it is burning it as a data file to the dvd and thus not being read properly when trying to view it instead of as an image file.

I do basically the same thing with manDVD, have it do the encoding and creating the menu then have it create an iso of the file output and burn that with K3b. Honestly can't think of a single time I had a problem except when my burner was dying.

---

### Post by Return Privacy on 2008-08-06
Thanks Brandel, for explaining those terms. It makes more sense now. I never knew that DVD playing isn't standard. I really like Ubuntu so far. I'm going to keep on learning, with the help of all you guys on this forum! I really do appreciate your help.:guitar:

---

### Post by brandonblm on 2008-10-11
If you go to the menu/system/adept(might say add/remove packages). you can type the package in the search field and it will pull it up for you. Then, click on the arrow and then click on install. Next, click on Apply at the top or the screen and it will install. This might help you with installing programs on your own. If you type in Tovid and find in the list 'tovid', you will get a program that uses a couple of other programs, but you have to do nothing but select the file to encode and then burn. It does everything for you. Give it a try, because it really is a little easier than using several different programs. 

Good Luck and Glad you made the Switch from MS!
Brandonblm

---

### Post by acreech on 2008-11-10
> **brandonblm said:**
>  If you type in Tovid and find in the list 'tovid', you will get a program that uses a couple of other programs, but you have to do nothing but select the file to encode and then burn. It does everything for you. Give it a try, because it really is a little easier than using several different programs. 


I had some issues with getting Tovid to work initially, but with the suggestions in [http://ubuntuforums.org/showthread.php?t=830499]("http://ubuntuforums.org/showthread.php?t=830499") I followed the directions from brcre and Tovid works fine now. 

This is a very basic program, but it has a GUI and it is easy to use. 

acreech

---

### Post by oldos2er on 2008-11-10
"MHO Ubuntu should make ALL programs complete with everything necessary to make them work when they are installed."

 That's the function of the package manager. I think some of the confusion comes from the fact that Ubuntu comes with several, e.g. aptitude, apt-get, Add/Remove Programs, and Synaptic Package Manager; and also the folks who are coming from a Windows mindset, i.e. they download a program from the 'net, then ask how to run it. It's understandable, of course, but (usually) the wrong thing to do in Linux.

---

