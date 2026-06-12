---
title: "how to view information about current network connection in Lubuntu"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by ask_ on 2011-11-26
Hello,

I am using Lubuntu 11.10. I wish to know how to view details of current internet network connection, i.e the data sent , data received and speed of present session. The connection information provides info on IP and DNS etc but not on speed,data sent etc.

In Ubuntu 11.10 , there is a system monitor, there one can view details of present network connection.

In Lubuntu 11.10 , all I found was a task manager, but it didn't give any details of the network session. Is anything similar to system monitor of Ubuntu , found in Lubuntu. Or will I have to install something from Synaptic. (a command in terminal would also be useful)

Thanks in advance.

---

### Post by ajgreeny on 2011-11-26
In Lubuntu 11.04 I have added the gnome-netstatus-applet with synaptic, and then added it to the Lubuntu panel.  It works faultlessly.

I presume it is available for 11.10, but I am not sure about that, not having moved on to Oneiric yet as my main OS.

Maybe the move to gnome 3 has removed anything like that from the available packages.

---

### Post by ask_ on 2011-11-27
Thanks. I searched for gnome-netstatus-applet in synaptic ,  but didn't find it there. As you said maybe they have removed it from the default packages. I searched for it in Software center too.

Anyways, I seem to have found a work around, it doesn't tell net speed but it does give info on data sent and received.

system tools --> system profiler and benchmark ---> network ---> interfaces. 

is there a way to find out about speed of net connection ?

There are other gui tools available, but they are mostly gui versions of already available commands. So it would be great if there is a command to check net speed.

---

### Post by Rex Bouwense on 2011-11-27
Right click your wireless icon in the panel and choose connection information.  You can get speed from there.  Is that what you mean?
Rex

---

### Post by ask_ on 2011-11-27
> **Rex Bouwense said:**
> Right click your wireless icon in the panel and choose connection information.  You can get speed from there.  Is that what you mean?
Rex

Hello,thanks for the reply.

Yes , I tried it after you told to do so. It says 'unknown' in the speed field.(At least now I know where to look for speed info.) Any idea ,why it is not showing speed in KB/s?

I use a mobile broadband connection via USB.

---

### Post by Rex Bouwense on 2011-11-27
No idea at all.  Who is the provider?  Perhaps that is the problem.  I can get that information from several networks that I connect to and I am using Lubuntu 11.10 with all of the updates to include the kernel update.

---

### Post by Rodney9 on 2011-11-27
I use 'Conky' to know what my computer is using ie CPU Memory and up and down net.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Rex Bouwense on 2011-11-27
> I use 'Conky' to know what my computer is using ie CPU Memory and up and down net.

Does Conky display what the OP wants to know, i.e. connection speed of his network?  I don't use it so I do not know.

---

### Post by ask_ on 2011-11-27
Thanks for the replies.

I have Reliance Mobile as my service provider. It is an Indian provider.

Perhaps you are right, it must be a network provider thing.
But thing is in Ubuntu 11.10 , there is a tool known as system monitor, there network speed is easily visible.

So I thought maybe, in Lubuntu something analogous might be existing.

note, even in Ubuntu , if clicked on Wireless icon in panel,I gets unknown in speed field. But the system monitor tool in Ubuntu does the job well.

---

### Post by Rex Bouwense on 2011-11-27
> **ask_ said:**
> Thanks for the replies.

I have Reliance Mobile as my service provider. It is an Indian provider.

Perhaps you are right, it must be a network provider thing.
But thing is in Ubuntu 11.10 , there is a tool known as system monitor, there network speed is easily visible.

So I thought maybe, in Lubuntu something analogous might be existing.

note, even in Ubuntu , if clicked on Wireless icon in panel,I gets unknown in speed field. But the system monitor tool in Ubuntu does the job well.

Try downloading and installing GKrellM.  That may be what you are looking for.  It is in the repositories.
Rex

---

### Post by ask_ on 2011-11-27
I installed GKrellM , it showed network info all right but not speed. :)

I then installed a system monitor application from Software center. Because I have had good experience from it on Ubuntu, so tried it on Lubuntu and it gives speed info as well. :)

---

### Post by Rex Bouwense on 2011-11-27
Great.  Glad that you got what you wanted.  When I downloaded and installed GKrellM, I thought that it included speed.  I must admit that I was doing two things at once and you know what they say about multi-tasking (doing more than one thing at a time with less than stellar results).:popcorn:

---

### Post by ask_ on 2011-11-28
Thanks for the help.

Your help on other threads is also appreciated.

:guitar:

---

### Post by amjjawad on 2011-11-29
> **Rex Bouwense said:**
> Right click your wireless icon in the panel and choose connection information.  You can get speed from there.  Is that what you mean?
Rex

This is exactly all what I do too :)

---

### Post by ask_ on 2011-11-30
> **amjjawad said:**
> This is exactly all what I do too :)

Yeah,but the trouble in my case was that it shows 'unknown' in speed field. Probably , a Service provider side fault. But it got resolved when I installed a system monitor. The system monitor shows speed somehow.

:)

---

### Post by amjjawad on 2011-11-30
> **ask_ said:**
> Yeah,but the trouble in my case was that it shows 'unknown' in speed field. Probably , a Service provider side fault. But it got resolved when I installed a system monitor. The system monitor shows speed somehow.

:)

Yes, I'm aware of your case but was just sharing what I usually do :)

---

### Post by ask_ on 2011-11-30
:) .

Nice signature by the way, the LOST page is very useful for newcomers to Lubuntu(and Ubuntu/Linux,in general) like me.

---

### Post by amjjawad on 2011-11-30
> **ask_ said:**
> :) .

Nice signature by the way, the LOST page is very useful for newcomers to Lubuntu(and Ubuntu/Linux,in general) like me.

Thank you and I'm glad you liked LOST :)
Try to bookmark it and keep an eye on the first post (always) because I keep updating it.

If you need anything, let us know :)

Have you checked Lubuntu One Stop Group? :)

---

