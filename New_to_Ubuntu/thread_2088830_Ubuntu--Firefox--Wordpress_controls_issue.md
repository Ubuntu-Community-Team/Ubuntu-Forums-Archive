---
title: "Ubuntu--Firefox--Wordpress controls issue"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by rakhoush on 2012-11-27
My current setup is Ubuntu 12.04 / Firefox 16.0.2 / Wordpress 3.4.2

Am trying to work with a WP theme called Modernize. 

There are default option of image Sliders - Flex/Nivo available in the theme. In the setup page, the button "Select Media" when clicked is non-responsive and hence I am unable to upload images into the slider.  I am finding the same result with Chrome as browser on Ubuntu.

I have used the same theme with Wordpress 3.4.2 on a windows xp machine with Chrome browser and it seems to be working fine.

I am unable to understand the exact problem. Is it something to do with Javascript ? I tested my browser with websites like javatester.org and the javascript is running just fine. 

I wasn't sure which category should I post this in. I would appreciate any directions/feedbacks for diagnosing the issue. 

Thanks Rakhoush

---

### Post by weedwacker on 2012-11-27
I don't have an answer for you rakhoush, just a question.

Are you running Wordpress locally, that is, does it reside on you computer rather than at your ISP?

I'm trying to install Wordpress to run on my computer so that I can learn Wordpress without having to be online. Haven't succeeded yet.

Looking for your reply.

---

### Post by superdaveozzborn on 2012-11-27
I am having the same issue with WordPress 3.5-RC1 which is beta so I am assuming that its something still in the works. but yes I cant add any images in my posts nether because the add media button no longer works and have had no luck with google so fare..

---

### Post by cjhabs on 2012-11-27
I did this and it worked fine under 12.04:

**Install LAMP server**

sudo apt-get install lamp-server^
Note: the ^ above is **not** a typo
Reboot - may not be neccessary but to be on the safe side

**Install Wordpress**

sudo apt-get install wordpress
sudo ln -s /usr/share/wordpress /var/www/wordpress
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress docs.miles33.com
sudo chown -R www-data /usr/share/wordpress
**Important note: ** In the setup-mysql script the location of the Wordpress site is defined - here I defined server.domain.com

Then access [http://server.domain.com/wordpress](http://server.domain.com/wordpress)

The first time you access the Wordpress URL, you come to the Wordpress quick setup screen:
Then Wordpress is installed and brings you to the login screen.

This installed Wordpress 3.3.1

Note to log into the admin panel, use URL:
[http://server.domain.com/wordpress/wp-login.php]("http://docs.miles33.com:2223/wordpress/wp-login.php")
To login as a user, use URL:
[http://server.domain.com/wordpress]("http://docs.miles33.com:2223/wordpress")

Worked like a champ for me. HTH

---

### Post by rakhoush on 2012-11-28
@weedwacker, I am running the server on my own machine which cjhabs has posted the method for the same. 

@superdaveozzborn what i am trying to do now, is to try and edit the source and get the image onto it coz the images are typically taken from wp-content/uploads/<year>/<month>/<files>
I will update if I find some luck here.

Cheers

---

### Post by mastablasta on 2012-11-28
you could use firebug to see what the button calls and why the function is not reposnding.

---

### Post by rakhoush on 2012-11-28
@superdaveozzborn

Please check the image/gallery settings to see if you need to upload the images using "set featured image" or any other link beforehand.

And once your uploads are in place then you could possibly go to the pages and add images to the posts or slider. 

The confusion arises when there is a button to select media which doesn;t work. This is the reason it wasn't working because the idea of select media is to select from already uploaded images, which one needs to do from the main gallery settings.

After a long detour, I finally managed with the existing options.

@mastablasta thanks for your reply. I did use firebug but couldn't trace this issue as the images were not there to be selected, while the logic laid somewhere else to make the selection pool beforehand.

Thanks

---

