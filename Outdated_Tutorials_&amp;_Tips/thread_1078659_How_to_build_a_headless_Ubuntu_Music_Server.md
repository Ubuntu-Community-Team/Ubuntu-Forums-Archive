---
title: "How to build a headless Ubuntu Music Server"
date: 2009-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by bigskypenguin on 2009-02-23
For the last four years I've been listening to my CDs through a cheap three disc changer I bought at Wal Mart, a truly low budget impulse purchase. For the last couple of months it would stop playing CDs until I wacked it on the side almost as hard as I could, and then it would stagger on for the next couple of days. How did I find out it could be made to work again by wacking it hard on the side? Why, by wacking it hard on the side, of course. I say once a piece of equipment stops working, and cost under fifty bucks several years ago, wacking it really hard is a perfectly acceptable maintenance and repair technique. I learned this from my dad; he was a professional.

But finally the wacking became less affective and I decided to upgrade and splurged for some new equipment. I got a Sony STR-DE197 receiver/amplifier and four Polk Audio R150 bookshelf speakers. Again, not real high end stuff, but a significant improvement over the older equipment, and more importantly my hand would stop stinging.

I mounted the speakers in the four corners of the big room in my apartment where I work and the receiver on a desk on the other side from my workstation. I decided to use an old machine to build a dedicated music server, and take a shot at setting it up headless for space and equipment conservation. (And just to be really cool.)

Another motivation for using a separate box was to avoid burdening my workstation with the extra task of playing music while I worked, which would likely end up in the music being “snipped” when the CPU encountered a particularly stressful task, in addition to the potential constant “boing!” coming from the music speakers during a lively Instant Messenger conversation.

Imagine Morrissey singing, “What she asked of me at the end of the day... BOING!... Caligula would have blushed.” Takes away the Old Moz's self-deprecating humor, doesn't it?

The box is a pretty standard issue five year old PC bought off the Internet for about four hundred dollars. I installed Ubuntu 8.10 desktop and plugged in a headphone jack to RCA cable from the audio output on the computer into the CD plugs on the back of the receiver. I hooked up a flat panel monitor, keyboard and mouse and told all three not to get too comfortable, as their surroundings were strictly temporary.

The first configuration I tried was enabling the remote desktop on the music server (hereafter just called the server) and connecting to it from my workstation via vncviewer. This gave me a nice view of the server's desktop, but was rather slow to respond to mouse movements and clicks. In fact, and maybe it's because the server is an older, slower box, it finally got annoying enough to start me thinking of another solution.

Another, and very important impetus to find another solution was that fact that if the monitor was disconnected from the server it wouldn't boot. The display manager GDM looks for the monitor and if not found gives an error message and stops. I don't remember what the exact error message is, but that's not important because we're moving on. That part of the story is a painful memory and emotionally I just want to get beyond it.

I also installed Xvnc, thinking a VNC configuration was what I wanted. Again, I'm not going into details, but that's not what I wanted either. Here are the steps I took, albeit along a meandering path over several days, that got my music server up and going, and actually providing the stimulating auditory delights I'm listening to at this very moment. Your time will be much quicker, as I've already endured the pain and suffering for you, much like a soldier throwing himself on a grenade to save his comrades.

   1. Install the latest Ubuntu. In my case 8.10.
   2. Configure your NIC in /etc/network/interfaces (GDM seems to do this for you if you boot with it, but not if it's disabled)
   3. Install rcconf so you can enable/disable GDM as needed during configuration and testing
   4. Set up the mount point to your music collection if it's on another machine (Mine is so I'll include this step and explain why I did this later.)
   5. Configure X11 Forwarding to display the player on your workstation
   6. Install a player and ripper
   7. Log in and test 

**Step One – Install Ubuntu**

I'm sure everyone knows how to put a Ubuntu CD into the drive and get it up and installed, so that's step one.

**Step Two – Configure your NIC in /etc/network/interfaces**

My music server is far away from my 16 port switch everything else is hooked to, so I chose a Rosewill RNX-G300LX wireless network card for an interface. I've used them before, they're very reasonably priced, and they play very nice with Linux. I put the following into /etc/network/interfaces.

auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid CamarilloBrillo
wireless-key hex-key-value-of-wireless-router

One important note here. If your ESSID value from your wireless router has spaces in it, it won't work! Mine was originally called “Camarillo Brillo”, so I put the double quotes around it in interfaces but it would not connect. After quite a while trying other things I went ahead and renamed the interface in the router to CamarilloBrillo, took out the double quotes and the space, and bingo, connected right up.

**Step Three – Install rcconf for disabling/enabling GDM window manager**

You may need to disable/enable GDM a few times as you sort through the process of this configuration, and once you have rcconf installed, it's a breeze. Execute the following from a shell:

sudo apt-get install rcconf

(Personal note: I actually don't use sudo. I always just become root when I open a shell to save me the typing. I'm a wild man. I live on the edge.)

Once rcconf is installed you can run it from the command line and a textual interface appears that you can scroll down to GDM and hit the space bar to disable it. Next time you boot the machine it will come up to a shell's login prompt instead of the GUI log in window. If for any reason you need the full Gnome desktop back, just run rcconf again and check the box next to GDM. (It will appear at the bottom of the selections once it's disabled... go figure.)

**Step Four – Setting up a mount point for your music library**

I set up my music library on one of two FreeBSD servers I have here. That way, I can rip CDs from my workstation directly to the BSD server, and mount that file system from the music server, so I can also access my music from like a coffee shop I'm sitting at being hip and cool on a Sunday afternoon.

So I created the directory

/mnt/music on the music server and made this entry in its /etc/fstab file so that it would be mounted to the BSD server's music directory upon boot.

192.168.1.101:/usr/music /mnt/music nfs rw 0 0

There are many ways you could configure this, and the simplest might be to mount the server's music directory from your workstation so that you can rip the music from your workstation directly to the server. Anyway, the whole NFS file system concept is too deep to go into here, but if you visualize the layout of your LAN in your head, and maybe even on paper, you'll get the picture.

**Step Five – Configure X11 forwarding to display the player on your workstation**

Now you can set up X11 forwarding to display the player on your local workstation. Edit the file /etc/ssh/ssh_config.

Uncomment the line that contains FowardX11 and make sure it is enabled to read

FowardX11 yes

I saw on a couple of posts this directive referred to something like X11Fowarding, or similar syntax, but it should be clear whichever way it is phrased which one you want to turn on.

**Step Six – Install a player and ripper**

Ubuntu 8.10 comes with Rhythmbox installed for a player, and it would probably work, along with Amarok, another popular one, but I chose Exaile for mine. For a ripper, some posts I read said that sound-juicer comes installed on Ubuntu, but it was not on mine. So on the server you want to do something like

sudo apt-get install exaile

Just substitute the player of your choice for exaile if you want to use something different.

Similarly, on your workstation you want to install the ripper. I found sound-juicer to be very good and easy to use, so on your workstation you want to do

sudo apt-get install sound-juicer

Again, there are different ways to configure this environment, and it really comes down to preferences. The main thing to understand is that your music server is now a part of your LAN and that X applications can run on one machine and be displayed on another machine, because at its heart X on the *nix systems is a protocol, delivering content to display over a network.

**Step Seven – Testing your set up**

Now to test this bad low motor scooter.

Reboot the server with the monitor, keyboard and mouse still attached to make sure it all boots properly. If you've disabled GDM with rccconf it should boot past the Ubuntu splash screen and come to a login shell. If not, log into a shell and disable it.

Log in and check your network interface for access to the LAN with something like

ping 192.168.1.254

I always start by pinging the router since it's the closest thing to your server.

If that's okay, and you've mounted a remote file system to store your music with an entry in fstab check that with something like

ls /mnt/music

and verify that any contents of that directory appear.

Finally, test the player. For this you log into the server from your workstation, the machine where the player will be displayed. You'll also need to tell ssh you'll be forwarding your X display, so note the arguments to ssh below.

ssh -X sevans@192.168.1.42

That “-X” is very important! Left out your player will not display on your workstation.

Of course, you'll supply the IP address of the music server on your LAN where I've put in mine. You'll then be asked for a password (you'll need an account on the server, of course), and once logged in bring up the player with the command

exaile &

The '&' character tells the shell to run the program in the background, thus allowing you access to the command line while the player is executing. You should now see the player on your workstation's screen.

IMPORTANT! It's likely the player will not, at this point, be able to play music even though all looks fine. If so, it's because the user you logged into the server with is not in the same group that owns the sound device, so you need to either log in to the server as root (which I had to do), or use the command vigr to add your user to the same group as root, so it can access the sound device. (Hat tip to Rick Moen)

And now, to paraphrase the British, Robert should assume an avuncular role.

Once you've successfully ripped music to your library, logged into your music server and played it from your workstation, decapitate the server and put that monitor, keyboard and mouse to good use elsewhere. Your headless music server no longer needs them.

Of course when you boot it you need to give enough time for it to accept log ins. Mine takes about one minute and ten seconds to fully boot and be ready. And always remember to shut down properly from your logged in shell. As root, type

shutdown -P 0

(Shutdown, turn off the power, in 0 seconds)

Feel free to email me with any questions, ideas, witticisms of your own. I'm not a professional system administrator, which is probably obvious here, but a long time developer who plays admin because I run this popsicle stand.

And lastly, a colossal thanks to the Silicon Valley Users Group list serve, who not only lend me considerable assistance on a regular basis, but do so with a degree of patience I'm sure I don't deserve.

(I wonder if sys admins playing developer are as annoying as developers playing sys admin... doubt it.)

Skip Evans
skip  -- AT -- bigskypenguin --DOT-- com

---

