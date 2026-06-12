---
title: "Error message while trying to run Update manager and Synaptic manager"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by Peterfc on 2011-10-20
Hi

I am trying to do an update and when i do i get a message from the update manager. Also when i tried to open Synaptic manager i get an error message. Lastly when i try to access Ubuntu One i also get an error message. Three error messages seems strange.The screen shots are all in the order i have listed the error messages.

Thanks for reading my post


Advent Laptop. Unity 3Gb. ram 250 Gb hard drive.Celeron(R) CPU 743 @ 1.30GHz

---

### Post by Paqman on 2011-10-20
Right, couple of different problems there:
[LIST=1]
[*]The first one is fine. I'm assuming you've been adding some extra software sources? You've just not added the key for one of them, so it can't verify the security of the software. It will still install ok if that's what you want.
[*]You have a duplicate entry in /etc/apt/sources.list. It's best not to edit this file manually, for this kind of reason. You'll have t open the file and delete the duplicate line it refers to.
[*]This is a lot more cryptic. I'd suggest Googling and/or searching this forum and Askubuntu.com for the error message, someone might have run into it before.
[/LIST]

---

