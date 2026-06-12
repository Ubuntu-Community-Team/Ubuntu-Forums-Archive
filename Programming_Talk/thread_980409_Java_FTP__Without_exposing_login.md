---
title: "Java FTP  Without exposing login"
date: 2008-11-12
forum: Programming Talk
---

### Post by notamonopoly on 2008-11-12
So I created a small Java application to provide a way for users to upload files to my server and avoid timeouts over http.

It works great but the way I have it setup is that the ftphost, username and password are requested by the application after the app starts and the user successfully signs into their account. There really isn't anything stopping them from obtaining this information if they wanted, right?

I mean, if I decompiled the code and altered it so that the ftp login info was output and then ran it, I would obtain the info and have ftp access to the server.

I've been experimenting with JSch and sftp, but that doesn't solve the problem of having this info exposed.

So my question is, what is the best way to have an application (in any language) connect to a server securely without exposing the login information? Maybe I'm going about this all wrong.

I don't have root access to the server right now, but that can be arranged if a proper solution requires it.

Thanks

---

### Post by Phenax on 2008-11-12
(AFAIK)

You'll have to probably obfuscate the source code and use a secure connection. Java classes can be decompiled easily without obfuscation and you could easily use a network sniffer to obtain the information without a secure connection.

---

### Post by notamonopoly on 2008-11-12
Thanks for responding.

The problem is, no matter how much I obfuscate the code it is still very simple to find the location where a call to the server is being made and add a System.out.println (or whatever) and display the information that has been retrieved. Or for that matter you could debug the decompiled code and see it comming in live.

Any other thoughts?

---

### Post by Phenax on 2008-11-12
Well, in terms of obfuscation, I was in reference to a class obfuscater like Zelix Klassmaster. Zelix Klassmaster can obfuscate a class to a point wherein if one decompiles the class, it will not recompile cleanly, and all strings/variable names/(basically everything) will be virtually indeicpherable. It would take a huge amount of effort to reverse such obfuscation. But Zelix Klassmaster is proprietary, and probably quite a bit heavy for your project.

Then you have to protect from network sniffers.. which is equally as paining.

And no matter how much you do either, people will still be able to get the information, just takes a lot more effort.


Perhaps you can find an FTP server that can check for an FTP client "user agent", to make sure it's Java. It doesn't protect from other Java clients or spoofing, though.

---

### Post by shadanan on 2008-11-12
I think you are going about this problem incorrectly. As Phenax said, it isn't possible to completely hide the login creditionals if the client needs to use it to connect. By necessity, the client will at some point require the password in clear text in order to send it to the server for authentication.

I believe the solution to your problem is not authentication. It is authorization. You want to allow users to upload files, right? So, why don't you want them to figure out the login credentials? My guess is you wrote the Java program with the intention of restricting what the user can do once logged in. 

A better approach would be to configure the ftp server with an ftp "drop box" account that only allows uploads for instance. It depends, however, on what you're trying to accomplish and what type of security policy you're trying to enforce.

---

### Post by notamonopoly on 2008-11-13
Thanks for the responses, I was at work today and didn't get a chance to check the forum until I got home a few minutes ago.

I see your point about authorization and it would be perfect if I could automate the creation of a new ftp account for each user, but as I'm on a shared server I would have to go in and manually create them.

Currently I have one ftp account to "rule them all". The account is restricted to a particular directory which means my files are safe as they only have access to uploaded files. The application takes care of where to place the files during transfer within this directory, but if the user gets the login info, they would have access to all other user's files as well.

You can see my dilemma.

I was trying to think of an example of what I wanted and the closest that I could think of is the youtube app that allows you to upload videos to the site. I've never used it but I remember seeing the option on the website. The transfers must be done through ftp, or something like that. So how would they have gone about preventing anyone from getting the login info and getting direct access to all videos?

Oops, time to eat, I'll check back later.

Thanks again for your time.

---

### Post by SeanHodges on 2008-11-14
The problem with FTP is that it's not secure. Install [Wireshark]("apt://wireshark") and monitor the packets sent while running your Java program. You'll see the password appear in plain text. If someone wants to get the password for your FTP server, they are more likely to do it this way than to bother with decompiling the program.

If you want to secure the server that your program connects to, you need to introduce a layer of security to your transport. A client like [Jsch]("http://www.jcraft.com/jsch/") will allow you to connect via SFTP, which uses the far more secure SSH protocol for connecting to the server (whilst retaining the simplicity of FTP for transferring the files).

I haven't used Jsch before, thats just an example. But I'm sure there is an SFTP java library available that will be simple to use. A search on Google brings up a lot of options.

Another thing to consider: using SFTP allows you to use password authentication, and/or to use private/public keys (you can give each client a unique public key that you can revoke later if needed). The advantage of handing out public keys is that you have finer control over which clients can connect to the server. This is a big topic worth reading up on, but might be overkill for the purposes of your program. Either way, SFTP still allows secure password authentication, so you get the best of both worlds.

---

### Post by notamonopoly on 2008-11-14
Thanks for the tips.

I'm glad you mentioned JSch as I've been experimenting with it (mentioned earlier) and will continue to do so.

I guess there is simply no way to have one ftp account for all users without risking their privacy.

As it stands I will probably manually create new ftp accounts for each user as they request it, and will probably have to charge some sort of fee to cover the extra administrative costs. I really wanted to keep the site free, oh well.

I've learned a lot from everyone who responded, so thank you.

---

### Post by drubin on 2008-11-15
> **notamonopoly said:**
> 
It works great but the way I have it setup is that the ftphost, username and password are requested by the application after the app starts and the user successfully signs into their account. There really isn't anything stopping them from obtaining this information if they wanted, right?
Why not just have the FTP server configured to allow them to use their account details as the FTP login?  This way they do not need to know the "root" ftp login and you could disable their accounts if the need arose

What ftp server are you using?

---

