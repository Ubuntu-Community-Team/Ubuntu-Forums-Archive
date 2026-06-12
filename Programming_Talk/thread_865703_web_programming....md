---
title: "web programming..."
date: 2008-07-20
forum: Programming Talk
---

### Post by hockey97 on 2008-07-20
Hi, I made a php script that uploads files ect I am currently having trouble with permissions.

do you know what permissions supposed to be set??

I tried chmod 777 and currently I tried chmod 644 this is where I am at.

They all are not working any suggestions???

---

### Post by dominiquec on 2008-07-20
The execute permissions of the PHP script itself don't matter; the important thing is that the web process owner (usually www-data) can read the file.

The destination directory of your upload should be also be owned (and writable by) the web process owner.

---

### Post by Reiger on 2008-07-21
Yeah keep that in mind: the destination directory should have read/write privileges for anyone (which is 6 isn't it?).

Most definitely not execute permissions (unless you want people to run their apps from your web dir?!) ... 

So something like:
```

chmod -R 706 <my target dir>

```

Would be suitable. The -R switch recursively chmods all files inside <dir> also. You may even want to go as far as 606.

EDIT: And a good permission set for a PHP script would be 705.

---

### Post by hockey97 on 2008-07-21
ok, I will give that a try.

I had the upload php script working before. The problem was I made a admin page only for me to login which will allow me to manually delete any users pictures or files that are illegal. When playing with the script I was not able to delete stuff out of my mysql database. I looked for errors didnt' find anything until I saw the path name.

the path name is like this /home/linuxuser/websites/domainname/Users/$username/uploads/

that is the path name I see when my admin script tries to delete it now my admin delete thing script grabs the path name from the database and I check the database by loging in it and I only see that I saw above.

The path name is supposed to be like /home/linuxuser/websites/domainname/Users/$username/uploads/filename.extension

but only this /home/linuxuser/websites/domainname/Users/$username/uploads/
gets stored in the database for every file/picture stored.

however when I run my upload script I have it setup that it will echo out the path of the image where it's saved and it whould show the one with the filename.extension which is what I wanted. I was able to even check the folder physically and see an image in their with a image of a lock on the side of it.

Also got another questions: I just opened a gmail account to test my registeration script where it's supposed to submit a html e-mail to the user with a link to a script I have which will set the account to active.

I noticed that when I tested it. I would see from: www-data 

How can I make this somthing like [email]register@mydomain.com[/email] 

I have a domain name bought already and would like to make the person see a professional name other than www-data

would I have to config postfix?? got any good websites that would help?

---

### Post by hockey97 on 2008-07-21
problem fixed. not a permission problem my bad.

I am so stupid lol.

I forgot to also change the path to upload the file.

I made a $format  which I have a string in it like .gif which I wanted to add it on to the image ect.

I made the paths right when I display the link but I forgot to change the path name where the command is to upload the actual file.

---

### Post by hockey97 on 2008-07-21
ok now got another problem. I just notice this. When I upload an image I made it so that the user names would be uploaded to the database but just noticed that I would get nothing.


I am using sessions to pass from the login page to pass the user name which is supposed to be passed to each page however I am noticing that the user name dosen't get passed to other pages.

I would like how would you properly send a session value from one page to another.

I am using headers to redirect users to pages.

got any idea on how to  properly pass values to other pages?

---

### Post by LoneWolfJack on 2008-07-21
you probably are not using sessions correctly.

assuming you are using PHP, consider this:

page1.php
```

session_start();
$_SESSION['stuff'] = 'foo';

```

page2.php
```

session_start();
echo $_SESSION['stuff'];

```

obviously, for just passing some values, you could also use $_GET or $_POST.

---

### Post by hockey97 on 2008-07-22
ok I am doing that.  Some thing is wrong in my scripts that it's not passing the user name along.

What if I like made phpfile1.php that will set the sessions then pass them to phpfile2.php  would I be able to pass them to a 3rd page??

the login works. I have it setup so if the person didn't logout he will be still logged in and would have a session logged =1   this will allow him to bypass the login screen.  So  lets say that he logged in and was on my website then he typed in another website in the address bar then typed back my domain name which takes him back to the login but since the session stored a 1 so it will bypas the login and allow him to use his account page ect.

The problem is when I get to the upload file script page ect when I upload a image I get errors like stream could not be open and failed to move file ect  but then when I check in my mysql database I see a emtpy user name row but the image location would be in the image row.

I even when to the folder to see the image and I can't see any image file.

is it possible to reassign a value to a session.

I want to have code in the login that would check if the session user is empty and if so it will then  change the value of logged in to a 0 which would cause it to bring up the login form.

---

### Post by zipperback on 2008-07-22
Information on sessions with php can be found on the following page.

[http://www.php.net/manual/en/intro.session.php](http://www.php.net/manual/en/intro.session.php)

There is a huge wealth of information and examples available on the php.net homepage.

- zipperback
:popcorn:

---

### Post by hockey97 on 2008-07-22
OK just fixed it.  I been searching my code debugging and found a if statement that if user="" then exit this was in my upload script and looks like  this messed up the code so I gave it a try and now everything works.

Thanks for the help and the replies.

---

### Post by hockey97 on 2008-07-23
I got another question. I currently tested my register script. In the script I have code where I send a e-mail message to the e-mail address supplied which will give a link to another script which will activate the account.
now I tested it with g-mail since aol and msn blocks e-mail from my computer. An so I find out the person gets an e-mail from my mail serve which is postfix and it only shows the From: www-data.  Now  I want to make the From:  to be From: [email]regsiter@mydomain.com[/email] I want the persont that registered to see that address other than www-data.

Would I have to config postfix or do I change with php?? if I have to config postfix then how do I do this?

---

### Post by mssever on 2008-07-23
> **hockey97 said:**
> I got another question. I currently tested my register script. In the script I have code where I send a e-mail message to the e-mail address supplied which will give a link to another script which will activate the account.
now I tested it with g-mail since aol and msn blocks e-mail from my computer. An so I find out the person gets an e-mail from my mail serve which is postfix and it only shows the From: www-data.  Now  I want to make the From:  to be From: [EMAIL="regsiter@mydomain.com"]regsiter@mydomain.com[/EMAIL] I want the persont that registered to see that address other than www-data.

Would I have to config postfix or do I change with php?? if I have to config postfix then how do I do this?

You set your headers through PHP. But that's not to say that you don't have to configure Postfix, as well. But Postfix isn't causing your incorrect From: header.

---

