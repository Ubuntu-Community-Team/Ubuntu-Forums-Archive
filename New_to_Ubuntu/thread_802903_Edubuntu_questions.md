---
title: "Edubuntu questions"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by iamclueless on 2008-05-21
Hi

im am looking at proposing getting Ubuntu into the school i work at.  all advice would be appreciated.

Ive been looking at the Edubuntu documentation and have realised that this has great potential for the pre-existing computer labs at our school.

However, i want to propose something a bit different to the school management team.  I would like to introduce a mobile computer lab (laptops on a trolly that can be moved to different classrooms).  the selling point of the idea would be 1)mobility 2)cost - open source software and using older machines.

the second point is important.

a thin-client and server set up with ubuntu eases maintenance of the machines.

however, if i want the laptops to run wirelessly, i understand that a  thin-client setup is not possible.

it looks like i would have to setup, maintain, and update each machine individually.... this is not practical at all, given that i would just be volunteering to do this.

so the big question is:

is there a way i can set up 15-30 older laptops (pentium 3s with 128 to 256 ram), have a particular setup in each one (i.e. guest account with specific permissions, only certain apps installed), and be able to keep them updated without wasting too much time????

at this point i am thinking the way to go would be an alternate install with the settings i want, remaster it and create an ISO, burn 10 copies of the iso and install!  so that gets me started...

how could i maitain these machines????

thanks

---

### Post by Inxsible on 2008-05-22
One option could be minimal installation and then simply copy pasting the commands to install the software that you want on those machines.

Here's a small tutorial on it [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

and here's where you get the minimal cd [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by iamclueless on 2008-05-22
yep that could work, but some of the settings i want are not simple installation of apps.  i would like to have a guest account created automatically with the install.

but really the initial install is not what i am worried about.

it is the updating that i need to make easier.  a few hours would be lost if i had to get the laptops out, boot into it with my account, run the updates -- wait. reboot all machines. turn off the machines, and put them away.

more ideal would be... students finish their session. i tell them not to touch anything. I do SOMETHING that updates all the machines at once or eventually.  They (or maybe me) put the machines away.

the SOMETHING part is what im not sure about.  Im guessing this requires me to run a script that would remotely access each machine, run the update command.

or i suppose i could create a dummy user account... all it does is run update and whatever maintenance scripts id like to run preconfigured to run without passwords (autoclean, deleting all trash, tmp files and thumbnails).  get the kids to log into that account. get them to log out. then log into their guest accounts.     wastes a couple of minutes for everyone, but better than me wasting all of mine :p

again, open to all suggestions

---

