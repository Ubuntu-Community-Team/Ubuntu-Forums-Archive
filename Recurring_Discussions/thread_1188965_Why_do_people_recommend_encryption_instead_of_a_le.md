---
title: "Why do people recommend encryption instead of a less-secure password protection?"
date: 2009-06-16
forum: Recurring Discussions
---

### Post by mwillams73 on 2009-06-16
Look guys not everybody is concerned about that level of security, Ive tried true crypt and sure if you dont want super hackers and thieves getting to it its great but i dont need it, I just want to password protect a folder so my kid wont go poking around in my porn collection! Is that so hard? Ive looked through many a thread and everyone is asking a simple question can you password protect a folder and if so how? And of course in true linux style every posted reply is " ENCRYPT IT !!!!!!!"

 Why would i encrypt something on my computer unless its a high level security risk file, IE: social security numbers etc etc? I dont have anything on my computer that anyone would want(and if do have something they want they are more than welcome to it) but i do have some things that i dont want any child looking at. And yes i could create a new guest user profile but i dont want to.

I want to password protect a folder, thats the question and the answer to that question should be " Sure no problem just do this and viola your folder is password protected"  Instead its " Encrypt It!!!!!!!" Not to mention true crypt is not really that user friendly for noobs, But the uber geeky ubuntu forums couldnt possibly care about that could they? Maybe in the future you could try answering the question instead of suggesting something that the OP didnt ask for.

 Im pretty sure if the OP wanted to encrypt his file or folder he would have asked " How do I encrypt a folder?" 

Just a thought and only my opinion, I hope i havnt made anyone angry but im tired of searching through thousands of threads only to not find the answer because no one has really taken the time to answer the question, instead they offer something that wasnt asked for in the first place. 

So back to the question, How do you password protect a folder, ( and no i dont want to encrypt) be specific, dont say change your user thingy to 0700. ( like most people even know what that means let alone how to do it)

If you are going to post something like that explain how to do it not just: "change your user id to 0700". Remember just because you know to do it doesnt mean the OP knows how to do it! This should go for all threads but I guess nobody seems to care that many a thread are going unsolved and unanswered because the OP is looking for a specific answer and because they themselves dont know what to ask for( due to inexperience) they are walking away with a bad taste in their mouth.

Just an observation from a guy whose been using ubuntu for about a year , and spending many many nights on the forums trying to fix things for myself and if at all possible for others as well. But thats what I thought these forums were about. Helping others so they can help themselves and thereby giving them the tools to help others also.

But Im starting to thinks its actually this :

 Helping others by making it as hard as you possibly can so they become frustrated and throw their pc away and by a mac cause its easier to use thereby stifling freedom and creativity and free thinking and bringing about communism, plagues, locusts, the anti christ, and well you get the picture!

Sorry that was supposed to humor, but i think the forums have sufficiently sucked all the humor outta me at this point.

---

### Post by bodhi.zazen on 2009-06-16
So long as your children do not have root access and can not boot a live CD, Linux permissions will keep them out, you need nothing more.

Simply give your children their won account and , on your home directory

chown user.user ~/private
chmod 700 ~/private

user = you log in name

---

### Post by macvr on 2009-06-16
> **penguin-of-doom said:**
> Hey,
Is there a program for Debian that I could protect my folder that nobody can get into? I know the administrator can go everywhere, but I am the administrator ^^ so how can I protect a folder with a password?

regards,
penguin-of-doom

If all you want to do is password protect : check out this solution>
[HOW TO-Simple Folder Password Protect]("http://ubuntuforums.org/showpost.php?p=6777859&postcount=1")

---

### Post by nandemonai on 2009-06-16
> **mwillams73 said:**
> Look guys not everybody is concerned about that level of security, Ive tried true crypt and sure if you dont want super hackers and thieves getting to it its great but i dont need it, I just want to password protect a folder so my kid wont go poking around in my porn collection! Is that so hard? Ive looked through many a thread and everyone is asking a simple question can you password protect a folder and if so how? And of course in true linux style every posted reply is " ENCRYPT IT !!!!!!!"

 Why would i encrypt something on my computer unless its a high level security risk file, IE: social security numbers etc etc? I dont have anything on my computer that anyone would want(and if do have something they want they are more than welcome to it) but i do have some things that i dont want any child looking at. And yes i could create a new guest user profile but i dont want to.

I want to password protect a folder, thats the question and the answer to that question should be " Sure no problem just do this and viola your folder is password protected"  Instead its " Encrypt It!!!!!!!" Not to mention true crypt is not really that user friendly for noobs, But the uber geeky ubuntu forums couldnt possibly care about that could they? Maybe in the future you could try answering the question instead of suggesting something that the OP didnt ask for.

 Im pretty sure if the OP wanted to encrypt his file or folder he would have asked " How do I encrypt a folder?" 

Just a thought and only my opinion, I hope i havnt made anyone angry but im tired of searching through thousands of threads only to not find the answer because no one has really taken the time to answer the question, instead they offer something that wasnt asked for in the first place. 

So back to the question, How do you password protect a folder, ( and no i dont want to encrypt) be specific, dont say change your user thingy to 0700. ( like most people even know what that means let alone how to do it)

If you are going to post something like that explain how to do it not just: "change your user id to 0700". Remember just because you know to do it doesnt mean the OP knows how to do it! This should go for all threads but I guess nobody seems to care that many a thread are going unsolved and unanswered because the OP is looking for a specific answer and because they themselves dont know what to ask for( due to inexperience) they are walking away with a bad taste in their mouth.

Just an observation from a guy whose been using ubuntu for about a year , and spending many many nights on the forums trying to fix things for myself and if at all possible for others as well. But thats what I thought these forums were about. Helping others so they can help themselves and thereby giving them the tools to help others also.

But Im starting to thinks its actually this :

 Helping others by making it as hard as you possibly can so they become frustrated and throw their pc away and by a mac cause its easier to use thereby stifling freedom and creativity and free thinking and bringing about communism, plagues, locusts, the anti christ, and well you get the picture!

Sorry that was supposed to humor, but i think the forums have sufficiently sucked all the humor outta me at this point.

2 second google search turns up an explanation of what linux permissions are and how they work.

[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

This is a volunteer community, you're not paying for support. If you want your hand held in absolutely everything without ever having to look up some fundamentals on how computer systems work then Linux really isn't a good choice for you, at least not a free variant.

If certain people here are happy to help assuming a level of prerequisite knowledge then that's up to them (myself included), and you shouldn't be complaining about the level of support you get.

Personally I'm not going to give someone a lesson on basic computing concepts when that information is a simple search away.

If anything these forums are **too** easy on people.

I understand that not everyone wants to be a geek and understand absolutely everything about every piece of software written but there is a limit. Using a computer effectively requires some level of knowing how they actually work and the basic concepts that go along with that.

This is the Internet. There are 1000s of pages, forums, newsgroups etc that can tell you everything you could possibly want to know, without someone having to explain it yet again.

---

### Post by aysiu on 2009-06-16
I guess the issue is that a lot of Linux users and developers don't like fake security.

If something is a hole, we let you know. And if something offers real protection, we also let you know.

The idea of "password-protecting" a folder without encrypting it is silly. It won't be protected. And what's so user-unfriendly about TrueCrypt? If you double-click a file with a .tc extension, TrueCrypt will automatically launch and prompt you for a password? Is that complicated? Please explain how that's complicated.

P.S. I've moved this rant to its own thread. The OP of the original thread was already satisfied. No need to bump a week-old thread with your own agenda.

---

### Post by macvr on 2009-06-16
> **aysiu said:**
> I guess the issue is that a lot of Linux users and developers don't like fake security.



Hi,
seems my comment was moved from the thread>  Folder with Password...

since you had replied before me, i presume it was you... 

I'd like to know how my solution is different from the solution others have given, to change the user permissions? instead of using the terminal , i have created the launcher. bozhi.azaen has also given the same solution.

What the technical well versed staff dont seem to understand... is that encryption is not very essential to home users like me. I dont have any incriminating materials which i need to encrypt, so dont many users.

The basic need is to lock the folders by changing the permissions , so that when friends pop by to use the system , i dont have to be rude and say wait, i'll log you in as a guest user...

Well it is not perfect but enough. Just a temporary block.

And the user is informed about the method , so he surely knows what he wants...! Why do his choices have to be curbed?

Also aysiu, i dont think its a rant and have no agenda.  :/

---

### Post by juancarlospaco on 2009-06-16
> **bodhi.zazen said:**
> 
chown user.user ~/private
chmod 700 ~/private

user = you log in name

More simple like this: 

[LIST]
[*][B]sudo chown --verbose $USER ~/private
[*]sudo chmod --verbose 700 ~/private[/B]
[/LIST]

;)

OR

Ubuntu comes out-of-the-box with SeaHorse, so please use it,
its so easy to use, **just Right click--->Encript...**,
you have to configure 1 time, and you can use it several times,
and on another PC, and installations.
Ubuntu have their own Key Server *(keyserver.ubuntu.com)*,
and can Broadcast public keys on a wired/Wireless LAN too.
You can Encrypt and Sign all your files, 
...and your files on UbuntuOne too, 
to gain privacity and integrity.

You keep safe the private key and remember key's password.
and share everywhere your public key.

---

### Post by aysiu on 2009-06-16
> **macvr said:**
> Hi,
seems my comment was moved from the thread>  Folder with Password... All replies to the week-after bumping-with-agenda post were moved to a new thread.

> since you had replied before me, i presume it was you...  Yes, I moved it.

> I'd like to know how my solution is different from the solution others have given, to change the user permissions? instead of using the terminal , i have created the launcher. bozhi.azaen has also given the same solution. If the user doesn't have physical access, then it's probably fine. Your solution seems a lot more work than just using TrueCrypt, though.

> What the technical well versed staff dont seem to understand... is that encryption is not very essential to home users like me. I dont have any incriminating materials which i need to encrypt, so dont many users. I'm "technical[ly] well[-]versed" for proposing a GUI-only point-and-click encryption solution, and you're not for proposing a script that requires terminal commands?

> The basic need is to lock the folders by changing the permissions , so that when friends pop by to use the system , i dont have to be rude and say wait, i'll log you in as a guest user... Well, if it's encrypted, you also don't have to log friends into a guest account.

> And the user is informed about the method , so he surely knows what he wants...! Why do his choices have to be curbed? I'm not curbing choices. I'm explaining why there isn't "a simple" way to password-protect a folder without encryption (and, yes, I don't consider your script to be any simpler than most GUI encryption programs, including TrueCrypt).

---

### Post by bodhi.zazen on 2009-06-16
Logging family / friends into a guest account is very easy, it is an option on the log out menu "switch user".

I prefer to do this as it prevents things such as accidental changes to my account settings, system settings, etc.

I personally keep firefox locked down, so the guest account has cookies , java script, flash, etc all set up for them so they can do as they wish in terms of email and browsing.

Guest accounts are simply more convenient for everyone, although I understand if you so no wish to use them.

In terms of the debate, I think part of the issue is education. If you are migrating from windows, linux permissions may seem inadequate at first. 

If a guest account is not an option, then I suggest you make the directory in question owned by root and access it with gksu nautilus. You will be asked for your log in password ;)

So the next issue is learning new tricks to accomplish what you want as seamless as possible. I am sure there are many many other ways to accomplish this simple task.

The next issue in the debate is more for the (admittedly paranoid) geeks. Security is always a balance of convenience and security, so your choices may vary. If you need to limit access to data you need to use encryption, otherwise the data is available with a live CD.

So I think the debate comes down to just a few things :

1. Learn how to use Linux permissions. Linux is not windows and really does not require password protected directories. This function is accomplished by permissions, possibly by adding acl (access control lists, or finer gained permissions).

2. Give each use a separate account. This principle holds true of any OS, and even Windows has a guest account. Now if you choose not to use this feature, whose fault is it then that guests have unfettered access to your account ?

3. Decide how paranoid you are, how sensitive your data is, and how much security you wish to add.

4. At least familiarize yourself of the advantages / disadvantages of the various choices.

Once you are able to do these simple tasks you should be good to go.

---

### Post by like coffee on 2009-06-16
Please don't use root account to watch porn.
Or anything other than administering your box.
Overkill is better than underkill use truecrypt,

it's a simple tar.gz with an windows style installer inside.
Nice gui and supports keyfiles, so you dont even have to 
remember a password.

---

### Post by Bodsda on 2009-06-16
> **like coffee said:**
> Please don't use root account to watch porn.


Why not? It's just another account with unlimited access to the system, posts like that go against one of the main principles of linux, 'choice'. If I want to use root for everyday activities then I should be allowed to. If the forums wish to discourage it due to the risks it causes then fair enough, but asking people not to do it I think is just wrong. At least point them to some resources explaining the risk of running as root.

Just to touch on the specifics of your post, watching porn has no extra risks then watching an illegally obtained film and if I bought the material from a shop then there is barely any risk at all, the fact that it is porn should have no influence to someones decision to run applications as root.

@ OP

I have seen many a thread asking the same thing and as you correctly said I have seen many a reply suggesting encryption, in fact this is the first time ive ever seen a link to a relevant resource regarding password protected files, however I think you must realize that encryption isn't reserved solely for highly sensitive files, if I wanted to stop someone from seeing my old schoolwork I could encrypt it as easily as I could encrypt my online banking pin file. 

I think encryption is seen by the uneducated party as being over the top but if said party took the time to understand the idea behind it they would realize that it is just another useful bit of technology designed for privacy. 

Regards,

Bodsda

---

### Post by jenkinbr on 2009-06-17
I tend to put some of the files I want hidden in a hidden permission-less root-owned directory.

```

mkdir .locked
mv file1 file2 file3 .locked
chmod -R 000 .locked
sudo chown root:root .locked

```

That code will move three files (file1, file2, and file3) into a hidden directory called .locked.  Next, I change the permissions on that directory and all child items of that directory to nothing for anyone. (removes read, write, and execute (execute is needed to do a directory listing)).
Finally, to password protect it (mild), I change the owner to root using chown.

To undo this: 
```

sudo chown jenkinbr:jenkinbr .locked ### Replace jenkinbr:jenkinbr with your personal username:group
chmod -R 700
mv .locked locked ### Optional - ctrl+h in nautilus makes hidden folders and files visible
```

Yes, I admit this is pretty low security, you can do a bit more to make the problem even less;
[list][*]Password protect your bootloader
[*]Password protect your bios setup utility
[*]remove the cd-rom boot option(s) from the boot sequence (they can be added later)[/list]

For anything that needs true security, I'd reccomend encryption.

---

### Post by Odemia on 2009-06-17
The point about choice is valid the choice is yours and now you have a few ideas.  Do as you please.  To your original question about why you are being guided to encryption, I don't think it has anything to do with "uber hackers" or anything like that, it is because those who are responding know that a password is not secure or protected.  Instead people are generally responding to your problem with the best fit solution, easy and protected.

IMHO your kid is probably better than you with a computer or will be very soon, kids learn fast and in your case they are growing up with a linux box in the house.  If they have any desire to learn about computers they they will outstrip your understanding/abilities in no time, this is assuming they haven't already.

If someone knows what they are doing it should take less than 10 minutes to get into a root directory without having to know the password.  Most of that time would be spent deciding exactly how much to cover their tracks.  A regular computer user with any aptitude for using google and the ability to follow instruction could probably do it in ~30 minutes (this is an estimate based on the availability of information I found searching google, I knew more or less what I was looking for and found detailed instructions in about 5 minutes) most of that time would be spent googling.  Don't believe me?  Try googling for things like "reset linux password", when I did it the top four results had step by step instructions that would get anyone who followed them root permission.  Only thing left to do is refine the method to cover your tracks.  If you still feel a password is safe enough at least now you know.

You can say that "we" are paranoid for discouraging password protection but you came to use asking how to protect your kid from your porn collection.  I don't think I am alone in believing that your simple password security/protection is no protection at all.  Just because it looks protected to you means nothing to me, your kid or anyone else.

---

### Post by jenkinbr on 2009-06-17
> **jenkinbr said:**
> I tend to put some of the files I want hidden in a hidden permission-less root-owned directory.

```

mkdir .locked
mv file1 file2 file3 .locked
chmod -R 000 .locked
sudo chown root:root .locked

```

That code will move three files (file1, file2, and file3) into a hidden directory called .locked.  Next, I change the permissions on that directory and all child items of that directory to nothing for anyone. (removes read, write, and execute (execute is needed to do a directory listing)).
Finally, to password protect it (mild), I change the owner to root using chown.

To undo this: 
```

sudo chown jenkinbr:jenkinbr .locked ### Replace jenkinbr:jenkinbr with your personal username:group
chmod -R 700
mv .locked locked ### Optional - ctrl+h in nautilus makes hidden folders and files visible
```

Yes, I admit this is pretty low security, you can do a bit more to make the problem even less;
[list][*]Password protect your bootloader
[*]Password protect your bios setup utility
[*]remove the cd-rom boot option(s) from the boot sequence (they can be added later)[/list]

For anything that needs true security, I'd reccomend encryption.
I forgot to mention that it would also be wise to build your case out of 3/4 inch steel and equip it with a safe lock :)

---

### Post by starcannon on 2009-06-18
For the most basic security, simply setup seperate accounts; remove read/write/execute access by any other account to your account; problem solved. 

If someone has physical access to your computer for extended lengths of time, there are no guarantees to privacy; I know many think otherwise, but the bottom line is, there is no such thing as safe.

If your trying to keep your kids from seeing your pron, then definitely create separate accounts, make yours viewable only by you, and don't leave any live CD's laying around; if someone is willing to boot a liveCD to view your pron, chances are they already have a pron pile of their own, further, they can view pron using a liveCD, see the circular and slippery argument here?  So, unless you are dealing with national security, or some other very sensitive data that could destroy you or the known universe, don't go crazy, just use the basic's and you'll have done fine.

Edit: +1 to NOT USING A ROOT ACCOUNT TO VIEW PORN, visiting porn sites while logged in as root is likely the most dangerous thing you could possibly think of doing, just don't do it, ever.

---

### Post by Viva on 2009-06-18
Probably not related, but how do you delete the history of files opened as root?:)

---

### Post by mwillams73 on 2009-08-02
Thanks to all of you, My intent with this thread was to open up real discussion about password protection versus encryption.

My secondary point is this, If my kid or anyone else for that matter is smart enough to figure out my password on a folder what would stop them from figuring out the password on the same folder thats been encrypted? 

Now do you see my point? Isnt it just as likely that if they can get into a folder thats password protected then they can also get into an encrypted folder that has a password. Which by my logic says that it doesnt matter which way you choose, Your screwed either way.

I also would like to see the option in future releases of Ubuntu to right clik on a file and set a password for it, surely this wouldn be to difficult to accomplish for the devs. For me Id like the option to do that , but you dont have to use it if you dont want to. Im not trying to stop people from gaining access to important documents just a roadblock.
If someones smart enough to get through then my liability as far contributing to juvenile delinquency is now not my problem.

As ive said before I used true crypt and yes it works but at the same time wouldnt password protecting the folder work just as well? It goes back to the if they can crack 1 password they can crack another regardless of whether the contents are encrypted or not. And if they have access to my PC when they do crack the password they now have the tools at hand to decrypt said files.

I found true crypt semi simple to set up but didnt really like the idea that if for some reason the police ever decided to look in my computer having encrypted files screams " something illegal's going on here" even if its just some hotties probing themselves. whereas a folder thats pass protected just says im a responsible adult with a four year who likes to play tux racer on my pc.

My child doesnt live with me and i only see her every few months, so why would i set up a guest account for the only other person who ever uses my pc? If the time comes that she wants her own I have no problem setting up her own box and showing her how to set it up. I already have a box ready and waiting for that day.

Please stop assuming that i know nothing and that i havnt done searches. Its rude and not becoming of the ubuntu community. My join date is not representative of how long ive been using ubuntu. I only decided to join because i want to help as best as i can. I also believe that only through discussion and debate and working together can we make Ubuntu better. Isnt ubuntu about freedom, options and helping one another?  Im only asking for an option that should be included that would help new users feel like they have even more options. besides Is right clik select password protect actually harder then setting up encryption or fiddling with permissions? I mean other than implementing it into the OS( which probably is hardy than downloading software to encrypt with.)

---

### Post by aysiu on 2009-08-02
> **mwillams73 said:**
> 
My secondary point is this, If my kid or anyone else for that matter is smart enough to figure out my password on a folder what would stop them from figuring out the password on the same folder thats been encrypted? 

Now do you see my point? Isnt it just as likely that if they can get into a folder thats password protected then they can also get into an encrypted folder that has a password. Which by my logic says that it doesnt matter which way you choose, Your screwed either way. No, you're misinformed.

In order to get to a folder that's just password-protected, you do not need to figure out the password. All you have to do is boot into recovery mode, boot a live CD, or remove the hard drive (to put in another computer or in an external enclosure).

In order to get to a folder that's encrypted, you actually have to know the password to decrypt it.

---

### Post by mwillams73 on 2009-08-02
You still dont get the point. One, im not misinformed I know about the recovery mode and using the Live cd, my point, as I'll reitterate once again for you, Is that if someone is already logged on whats the difference? 
And besides if my four year old is capable of doing either of those things without someone teaching her i guess I'll be signing her up for gifted classes this year. On top of that Im the only person I know who uses Ubuntu or linux of any kind, so Im pretty sure nobody i know could do either of those with much success.Let alone use a disk that they dont have. Or know how to even make the grub appear. (I could be wrong but Im probably not)

If they are logged in(by me) they have access to either file, encrypted or not and if they can crack 1 password whats to stop them from cracking the encrypted one? absolutely nothing thats what. so yes encryption is great for an intruder( someone breaking into your house or someone trying to boot into your system  without your knowledge),  but if you know the person and you logged them on then all bets are off.

Again this is not about keeping people out because im a paranoid person, its about a simple way of roadblocking someone from gaining access while i have my back turned for a minute or two. IE keeping my kid from looking at something she shouldnt while i go pee, and yet at the same time i can not worry about having to set up extra security that i dont need in the first place.( yes i know its relatively simple to do) 

My thought is that if you just want a simple password lock( without messing with permissions or encrypting) when you right clik on it you can select add password, and from then on whenever you try to open it, it asks for your password until you decide you dont need it. if someones logged in with your knowledge you dont have to worry too much about them looking at it. Im not worried about someone gaining access via booting up the live cd or the recovery mode.
What id like is to get a discussion going about how hard it would be to set this up and what we could do ( those of us who want it) to help the Ubuntu devs maybe get started on setting it up for the next LTS release.

---

### Post by aysiu on 2009-08-02
> **mwillams73 said:**
> my point, as I'll reitterate once again for you, Is that if someone is already logged on whats the difference?  The difference is that someone can log out and view your "password-protected" folder by other means but the *only* means by which someone can view your encrypted folder is by brute-forcing the password. > 
If they are logged in(by me) they have access to either file, encrypted or not and if they can crack 1 password whats to stop them from cracking the encrypted one? absolutely nothing thats what. so yes encryption is great for an intruder( someone breaking into your house or someone trying to boot into your system  without your knowledge),  but if you know the person and you logged them on then all bets are off. Exactly my point. If you trust someone with your computer then everything, including supposedly "password protected" folders are fair game because you trust them. If you don't trust them, that's when you use encryption because it actually keeps them out.

> Again this is not about keeping people out because im a paranoid person, its about a simple way of roadblocking someone from gaining access while i have my back turned for a minute or two. That's what separate user accounts are for. Lock the screen or log out. > My thought is that if you just want a simple password lock( without messing with permissions or encrypting) when you right clik on it you can select add password, and from then on whenever you try to open it, it asks for your password until you decide you dont need it. That's exactly what encryption does. Install TrueCrypt and you'll see that's exactly how it works. Once you've set up your encrypted volume you just double-click on it, it prompts you for a password, you enter the password, and it opens so you can see the files in the container.

So, yes, you are still misinformed even though you insist you're not. For simple security when your back is turned, you log out or lock your screen. If you want to actually go beyond that, that's what encryption is for. Encryption is not complicated. It's exactly what you seem to think "password protecting a folder" is.

Once you have things encrypted, just double-click and enter your password. It's password protected *and* really protected.

---

### Post by bodhi.zazen on 2009-08-02
OK, lets not use such fighting language :lolflag:

Basically, the idea of a password protected directory / folder is a Windows concept. In windows there is no such thing as permissions, so they came up with the idea of password protecting directories / files.

The problem is such protection is easily cracked.

On Linux the OS was built from the ground up to be multi user and basically everything is password protected. Each user should be given a unique account and if you allow others to use your computer, give them a guest account. The guest account has a number of other advantages such as profiles on applications (firefox) etc.

Now in Ubuntu you need to make your home directory private.

So in Linux everything is already password protected. it is called permissions.

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

To continue with encryption , encryption is the only way to secure your data, so when you want more then the defaults in Linux, ie when you ask for a "password protected" people will suggest encryption.

To answer your next question, really if your system is compromised, and somebody has physical access and/or a password to your account, your box is pwned. There are a thousand of ways they can obtain access to your data and the only things you can do to prevent this are 

1. encryption.
2. restrict physical access.
3. selinux or apparmor may be able to help.

But assuming somebody somebody has access to you computer or has a password to your account they have access to all your data via an almost endless number of methods.

Assuming your account has root access, either via sudo or su, if a user has physical access or your log in password they also have access to root.

This is different from privilege escalation, where a user has a unique account , say foo, and this second account does not have access to your account or root. The first case is not really provilage esculation as the user already has access to an account with root access.

---

### Post by mwillams73 on 2009-08-02
Boy you really are an ***, Im suggesting that we try and find a simple way to do something and you keep hounding me. please from now on asiyu keep your negative remarks to your self i didnt ask you to reply, And as ive noticed in the past youre not a very open minded person, which is fine. I posted on brainstorm since you feel youre so high and mighty, You must know everything right? Why do you hate being here, if you dont feel like walking people by the hand and babying us you are free to leave this thread you know.

Now if anyone else has anything "constructive" to add please feel free.
 



PS if this thread gets closed I'll know its because for some reason asiyu doesnt like me.

---

### Post by Tibuda on 2009-08-02
> **mwillams73 said:**
> Boy you really are an ***, Im suggesting that we try and find a simple way to do something and you keep hounding me. please from now on asiyu keep your negative remarks to your self i didnt ask you to reply, And as ive noticed in the past youre not a very open minded person, which is fine. I posted on brainstorm since you feel youre so high and mighty, You must know everything right? Why do you hate being here, if you dont feel like walking people by the hand and babying us you are free to leave this thread you know.

Now if anyone else has anything "constructive" to add please feel free.
 



PS if this thread gets closed I'll know its because for some reason asiyu doesnt like me.
aysiu post was really constructive in my opinion. Lock your screen when you leave the PC and use TrueCrypt if you want a password-protected folder.

---

### Post by mwillams73 on 2009-08-02
Thank you budhi, Thats exactly the kind of advice and constructive attitude that drew me to linux in the first place. Very nice Concise and to the point. I totally understand how ubuntu's permissions work, but Ive always wondered what It would take to implement something simple into nautilus that would allow something like i posted earlier. The reason I didnt like using truecrypt was after i encrypted a folder that folders size was limited ( IE you cant put more into it) at least thats how it worked in my case. Also although it was relatively simple to install and create the folder, i found that i couldnt easily figure out a few things, I cant remember what they were because at the time I thought that it was to much of a hassle to deal with it.  So I thought I might see if there was a simple way to password protect any regular file, without all the hassle. Asiyu swears that it soooooo simple but I didnt find it that simple.

I also know that a password is useless if someone has access to your session, but in my case its a four year old and a couple of friends ( who are not in any way tech savy at all) I really doubt the child could figure it out or that my friends would either. As I said  in my earlier post I posted this idea at brainstorm, and we'll see how many think that its useless, But atleast i tried. I really want to know what others think about the password lock, just to see who if any body would find it useful.

Feel free to check it out here 

[http://brainstorm.ubuntu.com/idea/20902/]("http://brainstorm.ubuntu.com/idea/20902/")

---

### Post by mwillams73 on 2009-08-02
> **danielrmt said:**
> aysiu post was really constructive in my opinion. Lock your screen when you leave the PC and use TrueCrypt if you want a password-protected folder.

Which I already know, My point of him being an *** was that he keeps saying that im uninformed, which i am not, I understand how permissions and user accounts work, I also understand how root access works. None of which is answering the question why is that all we have? I want to try and find a way to use true crypt or something like it integrated into nautilus so all anuone has to do is right click on a folder and select "add password lock". Im trying to find out whether or not people are interested in having this. I am not, on the other hand ,interested in hearing what i already know. Nor am I interested in mods telling me that they dont want to have to walk me through everything , especially when i never asked them to walk me through anything.  There is no reason to post the same information from the same mod over and over again. I get it Nobody wants anything more than what they have, so go ahead and close this thread. I think from here on in i wont log in anymore.

---

### Post by Tibuda on 2009-08-02
> **mwillams73 said:**
> Which I already know, My point of him being an *** was that he keeps saying that im uninformed, which i am not, I understand how permissions and user accounts work, I also understand how root access works. None of which is answering the question why is that all we have? I want to try and find a way to use true crypt or something like it integrated into nautilus so all anuone has to do is right click on a folder and select "add password lock". Im trying to find out whether or not people are interested in having this. I am not, on the other hand ,interested in hearing what i already know. Nor am I interested in mods telling me that they dont want to have to walk me through everything , especially when i never asked them to walk me through anything.  There is no reason to post the same information from the same mod over and over again. I get it Nobody wants anything more than what they have, so go ahead and close this thread. I think from here on in i wont log in anymore.
I understand now what you want.
If someone knows the command line syntax for TrueCrypt, it would be easy to create a Nautilus script for creating a password-locked folder with a right-click. Maybe this script was already made by someone.

---

### Post by ubuntu27 on 2009-08-02
Did you try [Kryptkeeper]("http://tom.noflag.org.uk/cryptkeeper.html")?

1) [Install Cryptkeepter]("apt://cryptkeeper")
```

sudo apt-get install cryptkeeper
```

2) Go to Applications menu/System Tools/Cryptkeeper

a new tray icon appears

3) Click on the new tray icon (usually a lock icon)

4) Click on New Encrypted Folder

5) Follow the instructions (simple things like choose the location of your password protected folder, and the name)

**

To acccess or to open your encrypted & password protected folder:

1) click on the Cryptkeeper tray icon

a list of ecnrypted folders will appear

2) Click on the name of the folder you want to access 

3) Type your password.

4) Enjoy

**

To CLOSE or to unmount the encrypted folder:

1) Click on the Cryptkeeper tray icon
2) Click on the name of the folder that is open

---

### Post by mwillams73 on 2009-08-02
> **ubuntu27 said:**
> Did you try [Kryptkeeper]("http://tom.noflag.org.uk/cryptkeeper.html")?

1) [Install Cryptkeepter]("apt://cryptkeeper")
```

sudo apt-get install cryptkeeper
```

2) Go to Applications menu/System Tools/Cryptkeeper

a new tray icon appears

3) Click on the new tray icon (usually a lock icon)

4) Click on New Encrypted Folder

5) Follow the instructions (simple things like choose the location of your password protected folder, and the name)

**

To acccess or to open your encrypted & password protected folder:

1) click on the Cryptkeeper tray icon

a list of ecnrypted folders will appear

2) Click on the name of the folder you want to access 

3) Type your password.

4) Enjoy

**

To CLOSE or to unmount the encrypted folder:

1) Click on the Cryptkeeper tray icon
2) Click on the name of the folder that is open

So far this is the best thing ive tried , Thank you Ubuntu27. It took one minute to download and about a minute to create the folder, very simple and straight forward when im done with it i just deselect it in the crypt menu and it disappears completely. Now if we could get it integrated into nautilus it would be even better, but for the time being it does exactly what I want.

I know i said I wasnt going to come back and log in, but i got a warning for saying the butt word so i had to deal with that and while i was at it i thought id see if anyone else had any suggestions or anything. To asiyu I'm sorry i called you a name, but I dont think that you like being here and that erks me to no end. I also apologize to any one else who might have been offended. Im so tired of hearing mods say that they dont want to walk people through things, It is my opinion that if you dont want to do something then you probably shouldnt do it, That includes posting in threads that you dont want to post in. It also means keeping your mouth shut and moving on to something else. But thats just my opinion.

---

### Post by ubuntu27 on 2009-08-02
> **mwillams73 said:**
> So far this is the best thing ive tried , Thank you Ubuntu27. It took one minute to download and about a minute to create the folder, very simple and straight forward when im done with it i just deselect it in the crypt menu and it disappears completely. Now if we could get it integrated into nautilus it would be even better, but for the time being it does exactly what I want.


I am glad I was able to help you. :)

---

### Post by Dullstar on 2009-08-02
Well, don't see what I'd need it for, but I guess I know how to encrypt something.

---

