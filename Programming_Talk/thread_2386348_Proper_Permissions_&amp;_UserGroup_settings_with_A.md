---
title: "Proper Permissions &amp; User:Group settings with Apache, www-data?"
date: 2018-03-04
forum: Programming Talk
---

### Post by peppy3 on 2018-03-04
[COLOR=#000000][FONT=Times New Roman]mpm-itk[/FONT][/COLOR][SIZE=2]Greetings,


I&#8217;ve been moving a number of site users and websites over to a new hosting service, into directories like &#8220;/home/username&#8221; and site content in: &#8220;/home/username/domain.com&#8221;. When I created a user, it has it&#8217;s own group name which is the same as the username: username:username . These /home/username directories also have permission under username:username . Up until today, Apache seemed to work fine by setting these directories as the DirectoryRoot in the apache config files for each site.


PROBLEM: Today I moved a site that requires the PHP function fopen to write to files or save uploaded images. I had a ton of &#8220;permission denied&#8221; errors. I&#8217;ve been reading around on Google/StackOverflow and finding answers that don&#8217;t work, or bad answers like setting permissions to 777.


This is what I have done so far, adding each username to the www-data group, and assigning www-data as the group for each username/folder for the websites:

    ```

    sudo usermod -a -G www-data <username>
    sudo chgrp -R www-data /home
    sudo chmod -R g+w /home

```

This seemed to make everything work, but I'm not sure is this is the way it's supposed to be done. I am concerned about the permissions, as the directories are now set at 775 and the files are 664. These are different than what was usually on my managed Hosting Services VPS (755 and 644).


What is the proper way to set these up, I&#8217;m a little noobish with permission stuff like this with the websites.


Thanks
Kind regard

[B]EDIT:

[/B]I found that www-data with 755 and 644 does open/read files, but cannot write to or create files. Another problem I found with assigning all usernames to group "www-data" (or changing all /home/* to www-data group, is that I could use fopen on "/home/user1/website1.com/file.txt" and display it on "/home/user2/website2.com/index.php". I'm not sure if this is secure or not. It's different than what my web host has it set up (even though theirs is also 755 for directories / 644 for files). Not sure how it's supposed to be done.

Does everyone else that administers Apache (with multiple users/domains) have permissions 775 for directories and 664 for files, with www-data as the group that owns the files and each user in the www-data group?

[B]EDIT:
[/B]
After studying more today, I should clarify that I am using the HTTP/2 mod for high web performance. I found that I need something like the [/SIZE]mpm-itk mod or suexec mod in order to separate users within www-data (if one website is hacked through wordpress for example, they should be prevented from accessing another site in a different user directory within the same www-data group). Is there any solution to this?

---

