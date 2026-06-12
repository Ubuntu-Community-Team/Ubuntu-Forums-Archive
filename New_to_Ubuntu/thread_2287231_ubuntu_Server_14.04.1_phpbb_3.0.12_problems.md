---
title: "ubuntu Server 14.04.1 phpbb 3.0.12 problems"
date: 2015-07-17
forum: New to Ubuntu
---

### Post by stonerrob420 on 2015-07-17
I have a old PC that has ubuntu server 14.04.1 installed on it with phpbb 3.0.12 forum running on it. Is there any way to remove the 3.0.12 phpbb server and reinstall phpbb3.1.5 on it with out wiping out the server? Keeping the databases and forums intact after reinstalling the phpbb forums software. Does the ubuntu software repositories have phpbb 3.1.5 in them where i can use sudo apt-get install command to automatically download the software and use it? :confused:

---

### Post by toxx on 2015-07-18
apt-cache policy phpbb3
phpbb3:
  Installed: (none)
  Candidate: 3.0.12-1
  Version table:
     3.0.12-1 0
        500 [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty/universe amd64 Packages

The version in the repo is the same one you have, so you'll have to download it from their website.
As for the upgrade, there are likely resources on their site which explain the upgrade process, you may not have to do a reinstall.

---

### Post by sandyd on 2015-07-18
If you installed from the repos, it should be upgradable, though I reccomend backing up first.

The main issue is that they scatter the files all over the place in the Ubuntu package.

First, backup these folders:
- /var/lib/phpbb3
- /usr/share/phpbb3
- /etc/apache2

Download phpbb 3.0.12 from [https://www.phpbb.com/files/release/phpBB-3.0.12.zip](https://www.phpbb.com/files/release/phpBB-3.0.12.zip) and extract to a clean folder.
Look around. In one of the folders, (likely /usr/share/phpbb3/www), there should be a config.php.

Copy that to the folder you just extracted (it should extract to phpbb3/ or to current directory). It should replace an existing file.
If you have any additional phpbb3 images (/var/lib/phpbb3/images folder) other than the default, copy those in the images folder of the extracted folder.
Copy everything in /usr/share/phpbb3/files over to the files folder in the extracted folder as well.
Copy any other additional stuff such as styles/etc over manually, but I reccomend doing that after you know it works.

Then, adjust the apache2 config in /etc/apache2/ to point towards the extracted folder. If everything is fine, backup the mysql database using mysqldump and then remove the phpbb3 package. Select "NO" when it asks if you want to deconfigure databases.

*Note
phpbb3 mods will be removed using this method.

---

