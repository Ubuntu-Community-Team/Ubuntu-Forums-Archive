---
title: "Suspend issue in 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Norm24 on 2008-11-01
I've been using a Gateway ML6230 laptop since Feisty and was never able to suspend(or hibernate).Upon resuming I always got the error message "failed to suspend properly".

Now when I try to suspend I get this message on a black screen:

"*stopping the firestarter firewall..."

At this point it just hangs and goes no further.

I was really hoping the suspend issues would finally be resolved in this distro.Its been the only issue that has kept me from removing Windows altogether from my machine.

Anybody have any ideas on how to resolve this?

---

### Post by Axos on 2008-11-01
I bought an HP notebook about a year ago and it had severe problems with suspending under either Vista or Linux. After putting up with this for months (kicking myself for not returning the notebook for a refund), a BIOS update appeared on HP's support page for my notebook and after installing it all the suspend problems went away.

So, check Gateway's site for a BIOS update for your model. It just might fix the problem (or not). Fingers crossed.

---

### Post by Norm24 on 2008-11-01
I have the latest BIOS for my machine.

Hopefully the Ubuntu team can resolve the suspend/hibernate issues with laptops someday.

---

### Post by Norm24 on 2008-11-02
Anybody have any suggestions?

Its amazing how the suspend/hibernate issues with Ubuntu in regards to laptops are almost universally ignored here and by the Ubuntu team.

If crappy Windows can do it flawlessly for longer than I care to recall why the hell can't this be resolved across the board on all laptop PCs that run Ubuntu?

Ubuntu is a GREAT OS...except for this issue.Its time to finally fix this so that ALL PCs can suspend/hibernate properly!

---

### Post by Norm24 on 2008-11-05
No one here really has any input on this at all?!

Amazing.:confused:

---

### Post by mp4215 on 2008-11-05
I'm having this issue also with a Gateway ML3109. In Hardy Heron it worked fine. Be patient, this will be fixed soon.

---

### Post by Norm24 on 2008-11-05
> **mp4215 said:**
> I'm having this issue also with a Gateway ML3109. In Hardy Heron it worked fine. Be patient, this will be fixed soon.

My patience is wearing thin...very thin.

I'll hold out though......for as long as my patience will,which won't be much longer.

Unfortunately Windows wins this round once again.

---

### Post by WelshChris on 2008-11-05
Sorry to report this, but suspend works perfectly with my Rock laptop in 8.10.  Previously I've had to fiddle about with the suspend scripts in /etc/acpi/suspend.d to get networking back up again after resume, but this time it's fine =(.
Sorry this doesn't help, though.

Are there any relevant error messages in /etc/messages?

---

### Post by gaspard.leon on 2008-11-05
don't know the specs on that machine, but if it's using AGP and nvidia, you can try NvAGP off (in hardy, not sure how intrepid interprets the xorg.conf)

if you don't know what I'm talking about, probably best to leave it until someone figures out the quirk for your hardware and it's fixed.

---

