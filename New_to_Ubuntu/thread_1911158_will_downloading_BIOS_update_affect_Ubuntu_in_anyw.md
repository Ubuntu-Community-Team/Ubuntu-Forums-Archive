---
title: "will downloading BIOS update affect Ubuntu in anyway?"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-18
Hi Guys
 
If I download a BIOS update from Dell for my Inspiron Q15R Laptop will this affect my current installation of Ubuntu 11.10 in any way or do I have to do anything?
 
What would be the procedure?
 
Regards 
Clive

---

### Post by wolfen69 on 2012-01-18
It will not affect your ubuntu install. A BIOS update is independant of any OS installed.

---

### Post by oldfred on 2012-01-18
Reinstalling BIOS changes all settings back to default. So if you did any changes to make USB keyboard work or SATA settings you may have to reimplement those.

I used camera to document all my settings as I could not take screen shots.

---

### Post by cliveT on 2012-01-18
Ok great - do I have to download it in any particular way, say through software centre etc. or just straight from Dell website?

---

### Post by cliveT on 2012-01-18
Thanks Oldfred - so does that mean it would effect things like any recent programs I have installed or nay things like installing  say "Thunderbird" etc.

---

### Post by oldos2er on 2012-01-18
> **cliveT said:**
> Ok great - do I have to download it in any particular way, say through software centre etc. or just straight from Dell website?

BIOS updates come from the manufacturer, you won't find them in Ubuntu's repositories.

---

### Post by wolfen69 on 2012-01-18
> **cliveT said:**
> Ok great - do I have to download it in any particular way, say through software centre etc. or just straight from Dell website?

The software center will not have bios updates. You will need to download it from dell, and transfer it to a floppy or usb flash drive.

---

### Post by cliveT on 2012-01-18
OK - is that all I do, just insert a disk and what?

---

### Post by Scott Baker on 2012-01-18
I have an addition to this question. I've seen a lot of these BIOS updates show up as Windows .EXE files. How is that handled in a Linux installation? What is the process for updating your BIOS in a Linux environment? :confused:

---

### Post by wolfen69 on 2012-01-18
> **cliveT said:**
> OK - is that all I do, just insert a disk and what?
I'm sure it is going to be in windows format, so you will probably need to take the floppy to a windows machine to transfer the file to floppy. I believe there is a way to do it from flash drive, but I've never done it. Can you give us the link to the dell website? I'll have a look.

---

### Post by Jerry N on 2012-01-18
Why do you think you need to update your BIOS?  Is there a problem that needs to be corrected or are you updating simply because an update is available?  Remember, if something causes the update to fail you might have to ship your computer back to Dell for repair.  Have you read and understood the BIOS update procedures?  Don't even consider starting the BIOS update process without having the instructions in hand.  On some motherboards (I know nothing about Dell) the BIOS update program runs only in Windows.  On others, the update can proceed from within the BIOS itself.  Very few, if any, motherboards will update their BIOS from within Linux.  

My advice:  Forget the BIOS update unless there is a specific problem that it will solve.

Jerry

---

### Post by mcduck on 2012-01-18
> **Scott Baker said:**
> I have an addition to this question. I've seen a lot of these BIOS updates show up as Windows .EXE files. How is that handled in a Linux installation? What is the process for updating your BIOS in a Linux environment? :confused:

You'll usually also find an alternative update package, either installable directly from BIOS itself or to be used as a bootable media of it's own.

---

### Post by syerges on 2012-01-18
> **Jerry N said:**
> Why do you think you need to update your BIOS?  Is there a problem that needs to be corrected or are you updating simply because an update is available?  Remember, if something causes the update to fail you might have to ship your computer back to Dell for repair.  Have you read and understood the BIOS update procedures?  Don't even consider starting the BIOS update process without having the instructions in hand.  On some motherboards (I know nothing about Dell) the BIOS update program runs only in Windows.  On others, the update can proceed from within the BIOS itself.  Very few, if any, motherboards will update their BIOS from within Linux.  

My advice:  Forget the BIOS update unless there is a specific problem that it will solve.

Jerry

I have to agree after having much experience with Dell from friends. Dell will let it break, and rather than help you, tell you to buy a new Dell and send you to a sales rep. Leave the working Dell be...

---

### Post by cliveT on 2012-01-18
> **syerges said:**
> I have to agree after having much experience with Dell from friends. Dell will let it break, and rather than help you, tell you to buy a new Dell and send you to a sales rep. Leave the working Dell be...

OK guys I`ll leave it for now and read through all your replies and consider carefully!

Thank you all very much

Regards

Clive

---

### Post by Fernhill Linux Project on 2012-01-18
Do not attempt to flash the bios if you are unsure.
Flashing the bios can kill your computer if it goes wrong. 
You should read the manufacturers instructions and as many articles on doing this from a non windows system as possible before beginning.
You may also want to have a bios recovery disc and instructions for flashing a dead computer ready.

That being said, it is a simple process and as long as you are confident and good at following instructions all should go well.
Good luck :O)

---

