---
title: "Connecting a 3 dongle"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-06-25
I have followed all instructions found and also tried following suggestions about unchecking the PPP protocols apart from the one needed. Initially without doing that my 3 dongle (pay as you go connected) but sometimes mobile broadband did not show up in the drop down menu. It seemed to be a matter of chance. Now I cannot get on at all with any of the above - things checked or unchecked. 

Is this just that the connection is slow? (This does not make sense, however, as I can use the dongle in my previous laptop with windows. 

(The newer laptop is Acer Aspire 6930g and the older Dell inspiron 1525. The Dell has windows but I installed Ubuntu 12.5 and knocked out windows on the Acer because it crashed and could not be restored anyway without paying a fortune to Acer.....)

For anyone who is having trouble with the Crystal Eye webcam, which seems to be a common problem when you try Ubuntu with Acer - I found that 'Cheese' in the downloads works ok - but is a bit slow.

Thanks, J

J

---

### Post by hamstermoon on 2012-06-25
I use a 3 Dongle a lot (boyfriend lives in a field in the middle of no-where) and have no problems with it.
 
Which version of Ubuntu are you using?

---

### Post by Jackalyn on 2012-06-25
> **hamstermoon said:**
> I use a 3 Dongle a lot (boyfriend lives in a field in the middle of no-where) and have no problems with it.
 
Which version of Ubuntu are you using?

I am using 12.4 and oddly it is working now. I have no idea why! I just hope if I log off it will work again. The add in is not showing as connected. It would be nice to be able to access that box thingy that tells you you are connected but 3 have never heard of linux or ubuntu

Rather amused at the conversation which went, " I installed a different operating system instead of windows." "Oh did you know you can get Windows?.":p

---

### Post by afhx on 2012-06-25
I have found Network Manger to very unreliable in making connections. Google for Sakis3G . copy the download instructions to the terminal  and press enter.  When installed
you need to select show icon. Then you just click on it.

---

### Post by Jackalyn on 2012-06-29
> **afhx said:**
> I have found Network Manger to very unreliable in making connections. Google for Sakis3G . copy the download instructions to the terminal  and press enter.  When installed
you need to select show icon. Then you just click on it.

Thank you for this. I am still actually trying to do it. I did find this which I do not really understand, but others with the same problem may.]

[http://linuxconfig.org/mobile-broadband-connection-and-sakis3g](http://linuxconfig.org/mobile-broadband-connection-and-sakis3g)

my main problem is the part of the script I tried is not recognised and you cannot copy and paste it into the terminal.

One odd thing I have found. The connection manager route works better if I put my phone beneath the modem to support it. Now I wonder if I would solve all by getting a newer modem! (maybe it increases the strength of the signal?)

---

### Post by afhx on 2012-06-29
If you are with 3 , ubuntu documentation tells me that Huawei 160G 'works out of the box' . Apparently, this model is exclusive to 3.With regard to my previous reply, I forgot that if the dongle is your only means to be on-line then the instructions I gave won't work ( if not , just select the appropriate platform, then click for the download instructions- they then  appear immediately below). However, you should be able to download the source from another computer, then install. Very reliable,and far better than Network Manager( I can only get it to work with inserting instructions in the udev folder)

---

### Post by afhx on 2012-06-29
[http://www.sakis3g.org/#i386](http://www.sakis3g.org/#i386). This is the location you need.download instructions( select as a bloc , paste into a terminal and press Enter)
wget "[http://www.sakis3g.org/versions/latest/i386/sakis3g.gz](http://www.sakis3g.org/versions/latest/i386/sakis3g.gz)"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive
now extract from sakis3g.gz to get sakis3g. 
right-click and select properties
make file executable
run in terminal
select more options
select
put short-cut icon on desktop
click short-cut icon
 Problems I have found with Network Manager. When trying to connect, it won't connect and tells you that you are off-line. When you click on the  icon again ( white shield-like)
you get no response whatsoever. Removing the dongle and reinserting sometimes enables you to connect but only for the whole  business of being disconnected when you trying to  connect again to recur. For this reasons I use sakis. However, if you use sakis, you must remove the entry for your dongle from the Network Manager( had Network Manager  working every time in 9-4, and 10-4  by adding config info in udev  folder but after  upgrade to 12-4 and getting problems I opted for sakis rather than spend days getting it too work reliably again )

---

### Post by afhx on 2012-06-29
Nearly forgot, you will probably modeswitch to be installed which is by default in 12-04.

---

### Post by Jackalyn on 2012-07-02
> **afhx said:**
> Nearly forgot, you will probably modeswitch to be installed which is by default in 12-04.

OK think I downloaded the right file now. How do I find this modeswitch in 12.4?- and having extracted the files, what do I actually do next. I right clicked and it wanted to open them in Calligra or Libre? 

I think I might be on the home run...........

Ironically had the longest connection ever today with the network manager. :KS:popcorn:

---

### Post by speedwlk on 2012-07-02
> **Jackalyn said:**
> OK think I downloaded the right file now. How do I find this modeswitch in 12.4?- and having extracted the files, what do I actually do next. I right clicked and it wanted to open them in Calligra or Libre? 



I think what afhx is suggesting is the usb-modeswitch package, which you can easily install [if it is not already installed] from Ubuntu Software Center or by your favourite installation method.

---

### Post by afhx on 2012-07-03
When I said modeswitch is installed by by default in 12-04 , I mean it already installed.; you don't do  a thing. Unless you have installed the synaptic package manager( recommended- and much better than  Ubuntu  Software  Center )  you won't see this. I don't think you have used the instructions I posted .  Please copy the download instruction to the terminal by doing this:
select them  then hold down CTRL then press c
go to terminal
Hold down Ctrl and press v
press enter
.  If you have done it right, we should have a  file called sakis3g. Right click to open it and select Run in terminal. .Or run this command in terminal:
sakis3g
 When there elect to put an icon (more options) on the desktop. Thereafter, you just click that icon. 
 You can't install modeswitch  and much else using Software Center. A short way to check is:
sudo apt-get install modeswitch 
 if it is already installed it will tell  you l, otherwise it will install it.
I hopes this helps.


If you have got the dongle working using Network Manager, it might be helpful for others if you could mention  the model number and name. If you get sakis to work, and you should, you might mention this.

---

### Post by Jackalyn on 2012-07-04
> **afhx said:**
> When I said modeswitch is installed by by default in 12-04 , I mean it already installed.; you don't do  a thing. Unless you have installed the synaptic package manager( recommended- and much better than  Ubuntu  Software  Center )  you won't see this. I don't think you have used the instructions I posted .  Please copy the download instruction to the terminal by doing this:
select them  then hold down CTRL then press c
go to terminal
Hold down Ctrl and press v
press enter
.  If you have done it right, we should have a  file called sakis3g. Right click to open it and select Run in terminal. .Or run this command in terminal:
sakis3g
 When there elect to put an icon (more options) on the desktop. Thereafter, you just click that icon. 
 You can't install modeswitch  and much else using Software Center. A short way to check is:
sudo apt-get install modeswitch 
 if it is already installed it will tell  you l, otherwise it will install it.
I hopes this helps.


If you have got the dongle working using Network Manager, it might be helpful for others if you could mention  the model number and name. If you get sakis to work, and you should, you might mention this.

Oh dear I did try!!

I seem to have several folders with sakis3g tar and gz and lots of sort of isolated files! Just had no idea where to go from there. I am going to try again. (Sorry to sound such a muppet but I do get there in the end!)

I realised this morning that copy and paste does not work on the terminal by using the keys which is very annoying.( I did know how to do that but you have to use the menus until I understand what to do about that by the way,-ubuntu 12.4)

I do have the synaptic package manager because it came with one of those Youtube 'Things to do after you installed Ubuntu' videos!

here is what happened in the terminal

wget "[http://www.sakis3g.org/versions/latest/i386/sakis3g.gz](http://www.sakis3g.org/versions/latest/i386/sakis3g.gz)"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive

I got to sakis3gz 1 being saved ok. Then the problems start.

I have a folder rather than a file. It wants me to extract- can do that

I can also see a file sakis3g.gz BUT that is where I am stuck. Right clicking does not bring up a way to 'run in terminal.' It reccomends calligra, libre office.......

Trying copying and pasting the file into the terminal.....clicking on it open in gedit text editor. Then it tells me there is a problem opening the file.......... 

Can you tell me where I go wrong. Thanks. :popcorn:J

OOOH wait a moment. Found how to 'run in the terminal!' I HAD downloaded the right file as when I did it all again it wanted to install over the one I had. A little puzzled how I downloaded penguins in various colours and sizes in the process, but AFTER I had deleted the connection in the network manager it suddenly sprung into life and produced a different looking lot of writing  3internet(3 UK GSM) which is the connection I saw on youtube associated with sakis3g and a T mobile dongle. I assume I am connected therefore by Sakis and just have to remember how I get to the 'run in terminal' again. Also lol what do I do with all the penguins holding dongles? (icons)? I assume they have something to do with it?

Thank you again!

---

### Post by afhx on 2012-07-04
finally getting there. First delete all your folders and files called sakis. Start with with a clear sheet. 
cd to the directory where you do  want to download to( say cd /home/something/sakis)
repeat the download instructions as you did before( don't worry  not knowing  how to paste in terminal- you know now)
go to the folder sakis
You will see sakis3g.gz
extract
you now have another files (two in total in the sakis folder)
sakis3g.gz and sakis3g
right click sakis3g to open
select run in terminal
in terminal select more options
then select create window shortcut
that it 
if you ever move sakis3g from the sakis folder, you will have to create a new window shortcut.
sakis has never failed to connect for me; has never  disconnected me without warning.
As you will see from the forums, problems abound with Network Manager as with regard to mobile broadband. Please keep on trying.

---

### Post by Jackalyn on 2012-07-04
> **afhx said:**
> finally getting there. First delete all your folders and files called sakis. Start with with a clear sheet. 
cd to the directory where you do  want to download to( say cd /home/something/sakis)
repeat the download instructions as you did before( don't worry  not knowing  how to paste in terminal- you know now)
go to the folder sakis
You will see sakis3g.gz
extract
you now have another files (two in total in the sakis folder)
sakis3g.gz and sakis3g
right click sakis3g to open
select run in terminal
in terminal select more options
then select create window shortcut
that it 
if you ever move sakis3g from the sakis folder, you will have to create a new window shortcut.
sakis has never failed to connect for me; has never  disconnected me without warning.
As you will see from the forums, problems abound with Network Manager as  with regard to mobile broadband. Please keep on trying.
:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:Dunnit...Have a Penguin on the desktop. Thank you :)

It will be wonderful to not be disconnected and play hunt the modem!

---

### Post by afhx on 2012-07-04
(I only added this in case chmod+x had not been done. Not needed if had been, or extract) Apologies I forgot a vital piece of information.You have file sakis3g. Right-click and choose properties. Now put a tick in execute permissions.  Now you will get run in terminal. I have added to my earlier instructions to give the complete instructions ( but ignore these additions  above if chmod and  extract have been  done ) Tried to add this to my last reply  but the edit button has been replaced by quote . Somehow, I inadvertently  put a lot of popcorns icons at the bottom of the message. So if you have a sakis3g just do this and keep one sakis3.gz

---

### Post by afhx on 2012-07-05
failed attempt to remove popcorn icons!

---

