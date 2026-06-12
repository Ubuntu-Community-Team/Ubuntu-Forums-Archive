---
title: "facebook API for my page"
date: 2010-11-05
forum: Philippine Team
---

### Post by xxxlam on 2010-11-05
Hi guys,

This is actually a school project, we are divided in several groups mostly 10 members.

The requirements of the project is as follows;
make and develop a community-based web site for Social Services Delivery. Our instructor adviced to download the facebook API for java and integrate to our page.

What comes into my mind is, a user will log-in into our page and use his/her facebook account... 

Maybe what I need is a tutorial, and/or samples on how to do so.

Please understand that I have a little knowledge in programming (hopefully, my groupmates will make it.)

THanks guys in advance. j3j3j3 :popcorn:

---

### Post by VirtualEdgar on 2010-11-05
You can start by going to this page -> [http://developers.facebook.com/docs/guides/web]("http://developers.facebook.com/docs/guides/web")

You must have knowledge on both HTML and PHP programming... even just a little. :)

Good luck!

---

### Post by loell on 2010-11-05
maybe, facebook's commenting system would suffice? ;)

[http://developers.facebook.com/blog/post/198](http://developers.facebook.com/blog/post/198)

---

### Post by enhu on 2010-11-11
i still have this in my files just when i bought an API from mporgsoft.
i did just earn a little to it then facebook banned me.

hope this is what you mean :P

```
1. Create a folder on your public_html directory to upload the files to.

2. Upload the contents of the folder 'giftapp' to this new folder.

Setup new app in facebook

3. Log into Facebook

4. Go to http://www.facebook.com/developers/createapp.php

5. Create a name for your app and agree to their terms

6. On the left side menu click on Authentication. 

7. For the field labeled Post-Authorize Callback URL enter (Changing yourdomain and appfolder to match your install) http://yourdomain.com/appfolder/newuser.php - Save Changes

8. Edit settings for your App again and click on Canvas on the menu

9. Fill out Canvas Page URL and Canvas Callback URL 

10. The Canvas Callback URL will look like (Changing yourdomain and appfolder to match your install) http://yourdomain.com/appfolder/

11. Still on this page change Render Method to FBML and Save Changes

12. Keep your app page open so you have easy access to your apps API Key and Application Secret



create Mysql database

13. Log into your hosting control panel for your domain

14. Create a new mysql database for this app

15. Log into phpmyadmin and select your new database. Import the sql file GiftApp_DB that was in with your files.



Edit files (Many of the files have notations explaining what the code does. Please read the notes)

16. Open up appinclude.php in notepad

17. Find $appapikey = 'apikey'; Replace apikey with your api key

18. Find $appsecret = 'appsecret'; Replace apikey with your app secret

19. Find $appcallbackurl = 'http://apps.facebook.com/demogiftapp/'; Edit to make this your app's callback url

20. Find $appcanvasurl='http://yourdomain.com/appfoldername/'; Edit to make this your app's canvas url

21. Edit the mysql database variables: "dbusername" 'userpassword' "dbname"

22. Find $AUID = "100000120560309"; and replace the number with your Facebook userid so you can access the admin features

23. Save file and upload



24. Open up appinclude2.php in notepad

25. Edit the mysql database variables: "dbusername" 'userpassword' "dbname" Same info you put into appinclude.php in step 21

26. Save file and upload



Your app should now be accessible and functioning. If it is not please contact us with a description of the problem.



27. Open up menu.php in notepad

28. Find 245370493217 and replace this number with your own Application ID

29. Save and upload



Banner 



30. Create a banner and call it banner.jpg, Upload to your app folder

31. Open header.php and edit the URL for banner.jpg to include your domain name and path to the image

32. Save and upload

33. If you do not want a banner shown delete the banner.jpg URL and the img tag









```

---

### Post by xxxlam on 2010-11-11
Thanks guys for the links you've provided, it's informative. Anyway, it's still prelims. Now, atleast, I got broader perspective on our project. I got to work now for the server side. 

I could not consider this as solved because the instructor always gives additional requirements...

---

