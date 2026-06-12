---
title: "What is ssh?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-18
I know I can get the info from google but I would to get the info from Ubuntu user itself. What does it do? In what condition or situation we need SSH? Any advise is highly appreciated:)

---

### Post by XCan on 2008-07-18
It enables one to remote into another computer "securily". Basically you can remotely control another computer.

---

### Post by schauerlich on 2008-07-18
> **wariskampar said:**
> I know I can get the info from google but I would to get the info from Ubuntu user itself. What does it do? In what condition or situation we need SSH? Any advise is highly appreciated:)

ssh stands for **S**ecure **SH**ell. Basically, it lets you get access to a computer other than the one you're on without having to physically be at the computer. This is useful for looking at the contents of your computer in the office from your laptop in the living room, doing remote work on a server, or accessing your files at home from work (although this requires some finagling with ports and such - but nothing to get into here.)

And, of course, here's the wikipedia article on it. :)
[http://en.wikipedia.org/wiki/Ssh](http://en.wikipedia.org/wiki/Ssh)

---

### Post by wariskampar on 2008-07-18
What is the different between SAMBA...Can I remotely control my wife laptop in real-time.

---

### Post by schauerlich on 2008-07-18
> **wariskampar said:**
> What is the different between SAMBA...Can I remotely control my wife laptop in real-time.

Samba is a file server. It's not related to ssh. To control someone else's computer in real time, you're probably looking for a VNC client.

[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

---

### Post by lisati on 2008-07-18
SAMBA is a Linux version of a Windows tool SMB (I can't remember off hand what it stands for)

And yes, it is possible to control another computer remotely - there are a couple of different ways of doing it.

The attached screenshot is from my laptop last Friday - it's running Ubuntu 7.04, while monitoring my desktop (which was defragging a disk at the time). (It was also installing Windows 98 in a "Virtual Machine" but that's not completely relevant to the question)

---

### Post by hyper_ch on 2008-07-18
> **wariskampar said:**
> I know I can get the info from google but I would to get the info from Ubuntu user itself.

In other words you were just too lazy to find out yourself what it is by using google and other online resources and you just hope you can ask the question here and get all info... basically you're asking that others make the work for you?

---

### Post by lazyart on 2008-07-18
To control a Windows PC from a linux machine, use Remote Desktop Client in either RDP or VNC mode.  Note that for RDP the windows machine will have to enable remote desktop from Control Panel>System>Remote.  For VNC, the machine must be running a VNC server.

For linux to linux, enable remote desktop sharing, then use VNC

For windows to linux, install VNC viewer on the windows machine, and enable desktop sharing on the linux box.

SMB = Server Message Block.  That tells little, but it's the protocol for sharing files.

SSH = Secure Shell.  Will get you a command prompt from a remote machine.  If you're versed in the command line you can do quite a bit.  If not you'll want to use VNC.

To get all of this to work across the internet you should look into port forwarding, as well as authentication and encryption/tunneling.  VNC is not one bit secure.  I haven't read much on RDP security... just consider that it's Microsoft's protocol....

---

### Post by muteXe on 2008-07-18
> **hyper_ch said:**
> In other words you were just too lazy to find out yourself what it is by using google and other online resources and you just hope you can ask the question here and get all info... basically you're asking that others make the work for you?

That's what forums can be used for.  Grow up and lose the attitude.

---

### Post by wariskampar on 2008-07-18
This VNC thing is readily available in Hardy Heron right. So if I want to remote control XP, I just need to install VNC on it. Then I can control XP from Hardy box and vise versa, right?

---

### Post by hyper_ch on 2008-07-18
> **muteXe said:**
> That's what forums can be used for.  Grow up and lose the attitude.

Or that's what forums and the kindness of other people can be **ab**used for ;)

---

### Post by wariskampar on 2008-07-18
You're right. I'm lazy. But I do not manipulate anybody to do any work for me. If the topic is not in your head, you don't have to reply. You don't have to be kindly enough to google it for me:) Asking is some sort of learning process and in fact asking the right person is the best! Just my 2 cents. By the way, is that the sole purpose of this forum. Asking the basic concept of Ubuntu, request assistance when stuck with problem etc... 


Anyway, I don't mind to be criticized.

---

### Post by hyper_ch on 2008-07-18
> **wariskampar said:**
> By the way, is that the sole purpose of this forum. Asking the basic concept of Ubuntu, request assistance when stuck with problem etc...

It is... but you were not stuck with a problem - as you did not even try to find out yourself ;) I think it's a courtesy to all people that spend their time to help others that you should at least first try yourself to solve the problems and use the tools available to you.

---

### Post by movrshakr on 2008-07-18
Well, my opinion is that forums are first and foremost to help people.  Almost every question asked on every forum everywhere has an answer somewhere else on the web.  The logic of 'don't ask here if the answer is somewhere else' would mean all technical forums should just shut down.

On the other hand, one realizes that the answers to questions in other forums is is actually the major source of "the answer is elsewhere."  So, if people there felt 'don't ask--go search' was the proper approach, the questions wouldn't get asked and answers wouldn't get documented...then we'd be totally dependent on manufacturer web sites.  I'll tell you this:  I have been more successful getting answers from kind people on forums than from mfg sites. 

So, wariskampar, you have seen that most people here are willing to help, rather than tell you to go away.  Ask away.

---

### Post by Vivaldi Gloria on 2008-07-18
> **wariskampar said:**
> I know I can get the info from google but I would to get the info from Ubuntu user itself. What does it do? In what condition or situation we need SSH? Any advise is highly appreciated:)

You can experience it yourself easily.

Start synaptic and install openssh-server. Now start a terminal and give the command:

```
ssh localhost
```

Answer yes to the question. Now you're in a ssh session. To exit it type exit. This is how your computer looks like when you ssh from outside. So you need to learn the command line a bit to make use of it.

Now in the default settings you may not be able to ssh your computer from the ouside. If you make some changes in the settings you can use

```
ssh your_computer_ip
```

from an outside computer to ssh your computer. So you can administer your computer remotely.

There are other things you can do with ssh. You can mount a remote folder as a local one using sshfs for example. This means that you can browse the folder (and your computer's contents) and use them from a remote computer as if it's a local folder. 

ssh is encrypted. You can even hide other type of connections in a ssh connection.

So it's one of the best tools around.

---

### Post by bab1 on 2008-07-18
For some clarity here (although not asked). ;-)  VNC will allow grapical control of another machine without the ability to copy to or from.  Samba allows copying (and removing or adding) to the remote machine, but only on shared files.

---

### Post by jaytek13 on 2008-07-18
> **movrshakr said:**
> Well, my opinion is that forums are first and foremost to help people.  Almost every question asked on every forum everywhere has an answer somewhere else on the web.  The logic of 'don't ask here if the answer is somewhere else' would mean all technical forums should just shut down.

On the other hand, one realizes that the answers to questions in other forums is is actually the major source of "the answer is elsewhere."  So, if people there felt 'don't ask--go search' was the proper approach, the questions wouldn't get asked and answers wouldn't get documented...then we'd be totally dependent on manufacturer web sites.  I'll tell you this:  I have been more successful getting answers from kind people on forums than from mfg sites. 

So, wariskampar, you have seen that most people here are willing to help, rather than tell you to go away.  Ask away.


Not only that, but telling people to Google it, or RTFM, is against the Ubuntu forum rules. I've noticed hyper has a history of doing this on these forums, however... why he hasn't been reprimanded is beyond me. I would just ignore his trolling.

---

### Post by cdtech on 2008-07-18
> **Vivaldi Gloria said:**
> 
ssh is encrypted. You can even hide other type of connections in a ssh connection.

What had failed to be mentioned, the most important about **ssh**, it is a secured shell.

Port 22 is the default port for **SSH** servers, it's a network protocol which allows data to be exchanged using a **secure channel** between the two computers.

---

### Post by bodhi.zazen on 2008-07-18
> **jaytek13 said:**
> Not only that, but telling people to Google it, or RTFM, is against the Ubuntu forum rules. I've noticed hyper has a history of doing this on these forums, however... why he hasn't been reprimanded is beyond me. I would just ignore his trolling.

hyper_ch has suggested people search, either searching these forums or using google. This is not a bad suggestion and is not against the CoC. Hyper_ch has not used personal insults or words such as "trolling".

I would suggest you examine your own posting style. In addition the preferred method is to use the report button to report posts that you think are in violation of the CoC and let the mods review the situation rather then take matters into your own hands.

---

### Post by hyper_ch on 2008-07-18
> **jaytek13 said:**
> Not only that, but telling people to Google it, or RTFM, is against the Ubuntu forum rules. I've noticed hyper has a history of doing this on these forums, however... why he hasn't been reprimanded is beyond me. I would just ignore his trolling.

well, maybe it's because I do help people on here ;)

Besides: Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime. ;) So I rather make people help themselves instead of spoon-feeding them.

But I still wonder what kind of attitude it is to ask for help and saying "I'm too lazy to do that". You might think this attutiude is great but think what this forum would be like if everyone had this attitude.

---

### Post by movrshakr on 2008-07-18
Well, *MY* attitude is...ask me.  If I know the answer, I will provide it--even if you are asking because you are lazy.

But that's just me.

From bodhi.zazen: [B][I]
A person with ubuntu is open and available to others, affirming of others...[/I][/B]

---

### Post by bhadotia on 2008-07-18
> **movrshakr said:**
> Well, *MY* attitude is...ask me.  If I know the answer, I will provide it--even if you are asking because you are lazy.

But that's just me.

From bodhi.zazen: [B][I]
A person with ubuntu is open and available to others, affirming of others...[/I][/B]

I all think this is simply unnecessary!
One should try to be gentle with others on the forum.

---

### Post by bodhi.zazen on 2008-07-18
I think my sig was quoted as an example of a helping attitude.

Both answering questions and teaching how to problem solve are acceptable methods of offering assistance and we should return to doing what we do best, helping each other.

---

### Post by bhadotia on 2008-07-18
> **bodhi.zazen said:**
> Both answering questions and teaching how to problem solve are acceptable methods of offering assistance and we should return to doing what we do best, helping each other.
;)Yeah!:mrgreen:

---

### Post by movrshakr on 2008-07-18
I'm all for it; let's help each other.  

Das ende.

---

### Post by cdtech on 2008-07-18
> **movrshakr said:**
> I'm all for it; let's help each other.  

Das ende.

That's what I'm talkin bout......:)

---

### Post by RavUn on 2008-07-18
Is there any way to use ssh to edit files?  You can move files around through the command line bug what if you want to check log files or edit config files... any way to do that with ssh without VNC?  I use nomachine and it works great, but I'd like to know if you can just use the ssh CLI.

---

### Post by Bachstelze on 2008-07-18
> **RavUn said:**
> Is there any way to use ssh to edit files?

There are lots of command-line editors available. You can use vi(m), nano, emacs or ed, just to name a few. To view the contents of a file, you can either use cat, which will just print the contents of the file, or less, which will let you browse throught it. Depending on what exactly you want to do, head or tail can also help you.

---

### Post by RavUn on 2008-07-18
oh yes, nano!  I always forget it's a command line editor.  I usually used gedit and always get confused when using vi.  Thanks.

---

### Post by wariskampar on 2008-07-19
These are what I gather so far; SSH is almost similar with VNC. SSH is mostly using command  and code while VNC is more toward GUI. SSH is more secure as it's name imply. However, we can make VNC more secure by tunneling through SSH. Hmm, before that, both programs are for remote control other system (and few other functions, transfer files???still confuse). On the other hand, SAMBA is another program by itself. As I'm using SAMBA myself, I would say, it is for sharing files and printer (haven't done yet) between machines.

If I use SSH/VNC, can my hardy box notifies me every time the remote system/machine log in (in my case if my wife or son turn on their computer). Meaning, evertime, they turn on their system, will SSH/VNC prompt a notification message in my hardy heron? Do I need their permission everytime I want to remote control / view their systems?

---

