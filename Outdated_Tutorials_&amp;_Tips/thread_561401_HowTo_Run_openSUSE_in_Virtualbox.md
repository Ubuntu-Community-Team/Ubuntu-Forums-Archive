---
title: "HowTo: Run openSUSE in Virtualbox"
date: 2007-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by raashell on 2007-09-27
Look it my Ubuntu beans and acknowledge at what level of experience I am writing this.  I don't believe in withholding information just because I don't know much.  With that said, the html version (easier on the eyes, easier to navigate, contains explanatory images), is here:

[http://www.oneuglyduck.com/vbox/]("http://www.oneuglyduck.com/vbox/")


Any problems you run into are unfortunately, your own.  Use and abuse at your own peril.


I am writing this as a means of giving back to the Innotek Virtual Box project. Their program saved my butt when I wanted to use Adobe Creative Suite 3 on Ubuntu. Instead of having to switch back and forth on a dual boot, they enabled my laziness by simply putting a little Windows XP program on my computer.

With that said, I can't contribute much, because I don't know much. What I do know is that I was unable to read their documentation, because it was written in a language that I do not understand-- techie guru language. This is a very basic layman's style guide, do not expect major revelations.

Also, this is written partly from memory, so if you get stuck there is a chance that I made a mistake and you may feel free to curse my good name with any number of colorful expletives.

The operating systems used in this HOWTO are Ubuntu Fiesty and openSuse 10.2. We will put Suse inside Ubuntu.

What is a Virtual Box

A box is techie guru slang for a computer. Hence, a virtual box is a virtual computer. Having a virtual computer is advantageous because you can load other operating systems on it, without having to partition your hard drive into a million little pieces (Did I read correctly that five is the maximum? Five pieces then.).

Innotek's virtual box is an open source program that is freely available under the terms of the GNU General Public License. It runs on Windows, Linux, and Macintosh and supports many different operating systems. So really, you could take this HOWTO, and modify it for use on your Mac, or Windows Vista, or Red Hat Linux OS.

Who is innotek?

Their website address is: [http://www.virtualbox.org](http://www.virtualbox.org) . Their description, from their web site, is as follows:

    innotek is a software company located in Stuttgart, in Southern Germany. Since its creation in 1992, a team of international software specialists has been focusing entirely on the development of high-tech system software. We have been involved in the development of PC virtualization technology form the very beginning and staff Europe's largest and most experienced team of PC virtualization software experts.

How To Get the Virtal Box

Enough talk already! Get to the action! Assuming you are one of those lucky dogs that has Ubuntu (you lucky dog you!) there are two main ways to get the virtual box. The easiest is to get on your Synaptic Package Manager, located in System > Administration, and search for "innotek." A package will come up that says "virtualbox," mark it, and install it. If it is not there, you may want to check and see that your universe and multiverse repositories are enabled. Click on Settings > Repositories and check both universe and multiverse (notice what it says in the description-- this is what you are getting into!). Then search for it again and install it.

The other main way is to go to the web site address, [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) , and download it. After that, when you double click on the file, being a fortunate Ubuntu user, it should start a file management program to build it. And if it doesn't, then you are an unfortunate Ubuntu user.

The command line to grab it is something like: sudo apt-get virtualbox, but I'm not sure because I didn't try.  There is a valuable wiki for this in the Ubuntu Documentation-- search it.

Once all this is done, you'll probably have to reset your mini-server-thing by restarting the computer or hitting ctrl-alt-backspace. After that, you should see it in Applications > System Tools > innotek Virtual Box.

How to start the Virtualbox

Mmmmmm.... Meat and Potatoes. Actually, this section is pretty much window dressing. Innotek designed a great program and it is largely self explanatory. When you start it, you will see the below, except without the XP and Linux programs in the toolbar.
Virtual Box Running Dreamweaver

Does that get your engine going? Dreamweaver running inside Ubuntu? God bless Linus Torvaldis.

Click on “ New ”, and follow the instructions. For example, this HOWTO explains how to install openSuse 10.2. I named it Suseroo, just for kicks(it could have been Susan, Sucily, and etc.). Then I selected the OS as a Linux 2.6 kernel, which it is, and hit next. Then Virtualbox asks for base memory in RAM. Suse has minimum requirements, but I'm too lazy to look them up, so I'll just give the program 600 and hope for the best. What this means is that, when I'm running the virtual box, 600mb of the 1600 of RAM I have will be allocated to the virtual box. Keep in mind what programs you will be running on the box. In my case, the Windows box I run gets a bit over a 1000, because that is what Adobe Creative Suite requires to run.

Here you may ask yourself, what if I jack it up all the way? The answer is that I don't know. Virtualbox is supposed to protect the user from his/her own idiocy, but I've never really put that to the test. ‹ - Literally, minutes after writing this I tried to mess around on my Suse virtual box, forgetting that I was in Windows. I think I asked for a few hundred megabytes of RAM more than my computer has. The result? Everything slooooowwwwwweddd down and stooooppppeeeedddd. Then Virtualbox aborted my windows box and everything sped back up. See? I'm an idiot, and I beat natural selection. I'm king of the world!!!

After you choose your allocation of RAM you get a screen asking for a hard disk. Virtualbox has a special type of hard disk that runs on what I like to call, “ Magic ”. It is the dynamically expanding image. Initially it is small, as you put more and more stuff on your box it gets bigger. Cool huh? I've never tried the fixed size option, but that might be a good choice if you have an external hard drive? When you choose the initial size, keep in mind that whatever operating system you are installing on it will detect that as the initial size. So if it is not big enough for the minimum operating system requirements, you will get shut down from the start.

So now you have the skeleton of your operating system set up and are ready to breath life into it.

Puting The Operating System In The Virtual Box

Before we start— while using a Virtualbox, right control frees your mouse to leave the window. Right control and "F" switch between fullscreen and window mode.

I spent all day and eleven cd's doing this, so bask in my extended suffering as I tell you what worked for me. First off, I downloaded openSuse in the form of a bitTorrent off of openSuse's web site, software.opensuse.org. It is a beefy download, five cd's in all, so I started it the night before and it was finished in the morning. If you don't have time for that, each cd downloads directly on broadband, at about a half an hour each. For the install, I only used the first three cd's.

In Ubuntu, set up a directory for your files, and double click the finished bitTorrent to extract them there. If succesful, you will have five files that end with .iso. These are image files that you would normally burn to a cd and use to initiate your new operating system. Don't waste your time and blank cd's doing this.
Now:

   1. Load up innotek Virtualbox
   2. Click on your new machine. Remember that I named mine Suseroo. By the time I was finished installing Suse, the name had changed to Susimillion for all my failed tries.
   3. Don't start it. Click on settings. On the left side you will see a list. Select CD/DVD-ROM.
   4. Change from “Host CD/DVD Drive” to "ISO Image File". Then browse to your first .iso file. It should have cd-1 somewhere in the title.
   5. Start er' up. You will get a start up wizard from Virtualbox.
      When you get to the installation media, at the bottom is " Media Source ". Select image file and browse to your first cd (same as above). Then click Next.
      Arguably, this may make the fourth step redundant. So what? Be redundant.
   6. Start the openSuse install. Do the basic, guided installation- I'm not covering that part.
   7. However, when you go to insert the " Second CD ", hit your right control key, or whatever you have set up to break the mouse from the virtual box, navigate to the top of the window and click on Devices › mount CD/DVD-ROM › CD/DVD-ROM Image. Then navigate to whatever iso file says " cd-2 ". In this manner, you switch cd's. This has the added benefit of being slightly faster, because you are not running off of cd's. (See the Below Image and note that this I am not running anything in the box, it's just there to show you where to go).
   8. In this manner you will install openSuse, and it will be good. Everyone will think you are a wonderful human being and say so. Once you successfully complete the installation, power down the box, and change the cd setting back to whatever cd/dvd was detected(this is in settings, in the main virtualbox window).

How did I use eleven cd's? I tried to run the installation off the cd's and it would get to the third one and then ignore it. I knew the download was good, because I did it three times. I checked the MD5 SUM and found that it was also good(though when the openSUSE installer scanned it, it didn't match!?). I searched thousands of posts on people using openSuse and people using Virtualbox with no luck. And then I went exploring and got lucky.
Moral of the story? The Dude abides.

An Aside: Guest Additions

Guest additions is a portion of the Virtualbox that is not automatically enabled. For certain things, it is necessary. For example, on my Windows box, if I want to move files from Windows to Ubuntu and vice versa I have to install guest additions. In this case, it sets up a shared network between the two operating systems. It seems like a no brainer, but I googled myself silly trying to figure out how to download guest additions. If you find that you need it to use a USB port, or share a network, it is in the Devices section of the window on your machine (not in the main interface, but the one specifically that surrounds your screen as you use it)

---

