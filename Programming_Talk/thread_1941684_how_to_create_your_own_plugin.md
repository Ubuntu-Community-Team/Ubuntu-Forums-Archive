---
title: "how to create your own plugin?"
date: 2012-03-16
forum: Programming Talk
---

### Post by hockey97 on 2012-03-16
Hi, I have coded small programs like a calculator in console and learned a little win32 api. 

Right now I need to create a plugin to all web browsers well the popular ones. The plugin is supposed to encrypt my source code of my website. 

ya, I know there are many other methods to do this... but when looking into them and talking with many gurus. They said the only good solution is to use a plugin. On person said to make it secure the plugin must have it's own javascript engine and html parser. 
To be able to encrypt and decrypt without giving any programmer a chance to take a peak at the encrypted data when it gets decrypted.

I have to ask here... what is needed to make the plugin actually make it very hard for hackers/programmers to get source code of my website.

---

### Post by ofnuts on 2012-03-16
> **hockey97 said:**
> Hi, I have coded small programs like a calculator in console and learned a little win32 api. 

Right now I need to create a plugin to all web browsers well the popular ones. The plugin is supposed to encrypt my source code of my website. 

ya, I know there are many other methods to do this... but when looking into them and talking with many gurus. They said the only good solution is to use a plugin. On person said to make it secure the plugin must have it's own javascript engine and html parser. 
To be able to encrypt and decrypt without giving any programmer a chance to take a peak at the encrypted data when it gets decrypted.

I have to ask here... what is needed to make the plugin actually make it very hard for hackers/programmers to get source code of my website.Ah, so you want to hide the source code of your website, and still have it displayed in a browser, after decoding it with a plugin? But... how do you make sure that  some debugger such as firebug won't display it? And how do you prevent Joe User from accessing the code of your plugin and use it elsewhere to decode your encrypted HTML? How do you prevent your site from being black-listed by all navigators because it tries to hide the page source code?

The real question to ask is what are you trying to protect that way? There is mus be a better way...

---

### Post by juancarlospaco on 2012-03-16
#FAIL idea dude...

---

### Post by Pierrick584 on 2012-03-16
Are you realy asking how to encrypt some HTML code...? seriously?

No offence, but i believe you might want to read a bit about how web server works, browsers... ect...

To sum it up, the end user never see your PHP code, unless you have some very huge security/code flaws, he can only see the HTML code, witch is completely harmless, even though you'd have a plugin to encrypt the html code, the user would have to use your plugin on his broswer, so he can not see the code, but at this point he could desactivate the plugin you know...

but realy, HTML has nothing but realy NOTHING that needs to be secured, and the user never see the php code of a website (or, just prove me wrong and try to get google's database info by "viewing" their source code from the browser ;) )

---

### Post by hockey97 on 2012-03-16
> **Pierrick584 said:**
> Are you realy asking how to encrypt some HTML code...? seriously?

No offence, but i believe you might want to read a bit about how web server works, browsers... ect...

To sum it up, the end user never see your PHP code, unless you have some very huge security/code flaws, he can only see the HTML code, witch is completely harmless, even though you'd have a plugin to encrypt the html code, the user would have to use your plugin on his broswer, so he can not see the code, but at this point he could desactivate the plugin you know...

but realy, HTML has nothing but realy NOTHING that needs to be secured, and the user never see the php code of a website (or, just prove me wrong and try to get google's database info by "viewing" their source code from the browser ;) )

Ya, I know how web servers work and browsers work. 

I use jquery and you can easily look at my source code and actually see the variables I am passing to my php code. I do know PHP is server sided. I never said I want to encrypt my php scripts. I said javascript and html source code. 

If you read my website you can easily see what I am passing or even guess. So I know if a hacker wants to have a way with my website they can easily do it. Just by reading the source code. 

I just want to make it harder for someone to actually be able to read the source code. For security purposes. 

I know html and javascript needs to be in the raw form for the browser to be able to parse it or run the code. So it needs to be encrypted and then decrypted . 

I was told their is just 2 ways to do this either do obfuscation... or write your own plugin. 

obfuscation can easily be be reversed. I was told making your own plugins is the only thing you can do to make it very hard for someone to reverse it.

I have seen a few websites that do have their source code encrypted and no not obfuscated. I even asked around to make sure since I am no expert.  I was told yes they encrypted it via their own plug because it would prompt you to install their plugin before viewing and if you don't they have a default page that tells you that to view the website you must install the plugin and also enable javascript to make sure the website will work properly.


So all you guys are saying the best I can do is just use obfuscation??
god kill me now!!! :(  so I guess my 5 years of work.. is pointless.


So then how do you guys prevent xss attacks to your website? 

I would think giving a programmer your source code allows programmers to steal your code and also allows programmers to help them attack your website.

---

### Post by CptPicard on 2012-03-16
> **hockey97 said:**
> 
If you read my website you can easily see what I am passing or even guess. So I know if a hacker wants to have a way with my website they can easily do it. Just by reading the source code. 

Then you're just designing wrong, taking security-critical issues onto the client.

> 
I just want to make it harder for someone to actually be able to read the source code. For security purposes. 

Real, genuine web application security does not try to climb the tree ****-first, to borrow a Finnish folk saying. If there is anything security critical in what you're sending to the client that you do not intend to trust, you're just doing it wrong.

> 
I have seen a few websites that do have their source code encrypted and no not obfuscated.

Examples? I have always been able to view the client-executable parts of all sites I've ever visited.

> I was told yes they encrypted it via their own plug because it would prompt you to install their plugin before viewing

Well, perhaps they have some incredibly special UI needs. So then they do write a plugin, but this has nothing to do with HTML source anymore really; the plugin probably just communicates with the server using its own protocol.

> 
 and if you don't they have a default page that tells you that to view the website you must install the plugin and also enable javascript to make sure the website will work properly.

Isn't it funny that they'd want you to actually enable javascript in your browser proper even when they are so security-conscious...

> 
So all you guys are saying the best I can do is just use obfuscation??
god kill me now!!! :(  so I guess my 5 years of work.. is pointless.


Yeah, I noticed you're still at this after all of *5 years* that you've been asking the question every now and then. You really must have some peculiar need to do this, one that I have not been able to grasp.

> 
So then how do you guys prevent xss attacks to your website? 

Well, for example, by sanitizing inputs by an HTML parser that allows whitelisted elements. It has nothing to do with what you're seemingly trying to do.

> 
I would think giving a programmer your source code allows programmers to steal your code and also allows programmers to help them attack your website.

You're only giving the client something that is representation-related. Nothing security-critical should ever go in there. I just get the impression you're just designing wrong, and have spent the past 5 years not learning the ways you actually, really, secure a web application.

---

### Post by juancarlospaco on 2012-03-16
The same CptPicard says.

Plus if you dont validate the JS, i can inject anything i want from client side to make your server crash

---

### Post by Pierrick584 on 2012-03-16
Ohh ohh!!! i got a good idea! do not use java script, stick to php only, that will most likely fix the problem.

---

### Post by Zugzwang on 2012-03-17
@OP: Please really reconsider whether you really want a plugin solution.

I don't want to kill the dead horse again, but there is one important thing that has been missing in the discussion here so far. Keep in mind that the user can always run something like wireshark to examine the communication between your web server and the browser. There is nothing you can do to prevent that, other than taking the site offline. This way, every hacker (or script kiddy) will be able to see what is being sent to your server and can use this information to prepare an attack.

So by having something like a "must-install" plugin, you will only keep people from your web site that do not want to install the plugin, while having pretty much no advantage in terms of security.

---

### Post by ofnuts on 2012-03-17
> **Zugzwang said:**
> @OP: Please really reconsider whether you really want a plugin solution.

I don't want to kill the dead horse again, but there is one important thing that has been missing in the discussion here so far. Keep in mind that the user can always run something like wireshark to examine the communication between your web server and the browser. There is nothing you can do to prevent that, other than taking the site offline. This way, every hacker (or script kiddy) will be able to see what is being sent to your server and can use this information to prepare an attack.

So by having something like a "must-install" plugin, you will only keep people from your web site that do not want to install the plugin, while having pretty much no advantage in terms of security.
As far as I understand it the OP expects to encrypt that...

---

