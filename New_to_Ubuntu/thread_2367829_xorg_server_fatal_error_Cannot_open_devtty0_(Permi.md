---
title: "xorg server fatal error: Cannot open /dev/tty0 (Permission denied)"
date: 2017-08-03
forum: New to Ubuntu
---

### Post by oschenker on 2017-08-03
Hi,
It seems like this is very frequent problem but my case seems little bit different and I can't use any solution described.
I am setting up AWS Ubuntu server to run Windows application. (I need AWS VPS but there is no Windos based LightSaile service).


I have installed wine package to Ubuntu 16.04. After I tried to start windows setup I have message:


> Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and start $DISPLAY set correctly.




After I tried to start X server using > startxI have got following error:


> Fatal server error
(EE) Parse_vt_settings: Cannot open /dev/tty0 (permission denied)


I am not ubuntu user at all so it is hard to me to find a solution. I have searched different forums and found out that problem is pretty frequent but solution is always different. Someone has created another user (not a mine case as I use username granted by AWS). Someone reinstalled X server (I did also but no success although).


Could some one explain me in plane English what shall I test in my system to diagnose the problem? Thanks.

---

### Post by vocx on 2017-08-03
> **oschenker said:**
> Hi,
It seems like this is very frequent problem but my case seems little bit different and I can't use any solution described.
I am setting up AWS Ubuntu server to run Windows application. (I need AWS VPS but there is no Windos based LightSaile service).

I have installed wine package to Ubuntu 16.04. After I tried to start windows setup I have message:

I don't understand what AWS means, but if you are using Wine to run a Windows application you are already looking for trouble. Wine will never be able to emulate the Windows environment perfectly so my advice is to really get a Windows machine to run what you want.

When you say "Windows cannot run a LightSaile service", I don't get it either. Seems like you are purposefully using Wine to run a Windows application, so how come Windows cannot run it? Sorry, it's just not clear to me. If something runs in Wine, it should also run in Windows.

> 
After I tried to start X server using  have got following error:

I am not ubuntu user at all so it is hard to me to find a solution. I have searched different forums and found out that problem is pretty frequent but solution is always different. Someone has created another user (not a mine case as I use username granted by AWS). Someone reinstalled X server (I did also but no success although).

Could some one explain me in plane English what shall I test in my system to diagnose the problem? Thanks.
Anyways, the error you are experiencing is weird. Maybe the error simply means your normal user doesn't have permission to start the X server. The X server starts by itself (by the user "root") when your computer boots. You don't have to start it manually.

So, there are many sides to your problem. First, what is AWS? Why do you want to run it in Wine in Ubuntu if you are not even experienced in Ubuntu?

If there are guides you are following you should link them here, so people trying to help you get an idea of what you are attempting to do.

---

### Post by oschenker on 2017-08-04
First of all, thank you very much for response. Please see my comments below.

> **vocx said:**
> I don't understand what AWS means

Sorry, AWS is just Amazon Web Services - virtual server renting service. LightSail - is a particular product - server type you can rent from Amazon with monthly payments.
I need this specific Amazon server due to location. Problem is that Amazon do not provide Windows servers in LightSail. So I have chosen Ubuntu.
> **vocx said:**
> ...but if you are using Wine to run a Windows application you are already looking for trouble. Wine will never be able to emulate the Windows environment perfectly so my advice is to really get a Windows machine to run what you want.

As I said above Windows machine is not an option here. Why wine? It was recommended by Windows software Vendor whos&#1091; software I need to run on Irelnd Amazon VPS. If you could recommend better solution, please, do it. I will appreciate! :)

> **vocx said:**
> When you say "Windows cannot run a LightSaile service", I don't get it either.

It might be a typo. I meant "Windows cannot run on a LightSail". Meaning LightSail doesn't provide Windows as an option.

> **vocx said:**
> Anyways, the error you are experiencing is weird. Maybe the error simply means your normal user doesn't have permission to start the X server.

It might be a reason. But I saw a lot of tutorials where some Windows (or other GUI environment) where setup on LightSail Ubuntu.
So I have concluded that somehow this permission might be requested and received. Although, I don't know how. I think I should do it inside Ubuntu (maybe create new user).


> **vocx said:**
> If there are guides you are following you should link them here, so people trying to help you get an idea of what you are attempting to do.

Sure. I used [this ]("https://www.metatrader5.com/en/terminal/help/start_advanced/install_linux")guide. It seems like completely missed the point as I had never seen reaction as described.
To install the wine I used [this ]("http://www.omgubuntu.co.uk/2017/04/how-to-add-wine-repository-ubuntu")page and [this]("https://wiki.winehq.org/Ubuntu") troubleshooter.

---

### Post by vocx on 2017-08-04
> **oschenker said:**
> First of all, thank you very much for response. Please see my comments below.
Sorry, AWS is just Amazon Web Services - virtual server renting service. LightSail - is a particular product - server type you can rent from Amazon with monthly payments.
I need this specific Amazon server due to location. Problem is that Amazon do not provide Windows servers in LightSail. So I have chosen Ubuntu.

As I said above Windows machine is not an option here. Why wine? It was recommended by Windows software Vendor whos&#1091; software I need to run on Irelnd Amazon VPS. If you could recommend better solution, please, do it. I will appreciate! :)

Sorry, I have no experience with that, so I cannot really help you further.

I just want to point out that the quality of the answer you get in this forum depends a lot on how you ask your question. People cannot guess everything you know or don't know so you have to state this in the beginning. Avoid using computer terminology if it is not immediately obvious to everybody. I think a term such as RAM and CPU is pretty standard nowadays, but things like AWS and LightSail are not widely known, so you should explain what they are before even asking your question.

> 
It might be a reason. **But I saw a lot of tutorials where some Windows (or other GUI environment) where setup on LightSail Ubuntu.**
So I have concluded that somehow this permission might be requested and received. Although, I don't know how. I think I should do it inside Ubuntu (maybe create new user).

Sure. I used [this ]("https://www.metatrader5.com/en/terminal/help/start_advanced/install_linux")guide. It seems like completely missed the point as I had never seen reaction as described.
To install the wine I used [this ]("http://www.omgubuntu.co.uk/2017/04/how-to-add-wine-repository-ubuntu")page and [this]("https://wiki.winehq.org/Ubuntu") troubleshooter.

I find it funny how you link to guides about installing Wine, which is fine, but you don't link to guides about your specific problem, namely the LightSail on Ubuntu situation. If you saw a lot of tutorials about this, you should mention them here as well, so people get a clear idea of the steps you are following.

Also, why are you using Ubuntu if you don't know the system at all? I have the impression you are blindly following some guide just to accomplish one objective, and using Ubuntu is just a stepping stone along the way. Ubuntu is an entire operating system, you'd be better learning more about it, instead of just focusing on solving one problem. Instead of asking your question as "I can't open /dev/tty0", you should explain with more detail exactly what you are trying to achieve and then maybe somebody will provide you an alternative: "I'm trying to set up a virtualized server in order to share a website with my company that is located in Ireland, but I also need it to have VPN support for clients in USA, and besides I want to stream some radio, and would like this to be port forwarded to my grandma's house and my cellphone at the same time, but without breaking the laws of physics and chemistry".

So explaining your problem in full detail is better than just focusing on a small part of it.

---

