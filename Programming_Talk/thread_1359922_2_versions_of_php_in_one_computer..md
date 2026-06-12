---
title: "2 versions of php in one computer."
date: 2009-12-20
forum: Programming Talk
---

### Post by aklo on 2009-12-20
Some questions to verify here.

1. Are there any programs similar like WAMP on windows?

Note: FYI WAMP is a program which lets you install apache, mysql, php all in 1 installer with no need for configuring. This is different from LAMP. Also WAMP allows me to install 2 php versions so i can switch them in just 1 click. I'm not sure about linux though...but if there is no automated process to do it...then it seems like a difficult thing to do.

2. How do i install 2 PHP versions if i'm going to do it manually...i don't suppose i can just download the 2 different versions and just run it?

3. Why did apt-get installed php 5.2.10 instead of php5.3?
I am unable to find php5.3 from the synaptic package manager and from the command line (well they are the same)

4. If i were to install php from source how can i do it?

PS: After i finished typing i did 1 last search and found this 
[http://www.brandonsavage.net/installing-php-5-3-on-ubuntu/](http://www.brandonsavage.net/installing-php-5-3-on-ubuntu/)

You got to be kidding me...tons of gibberish to type just to install php 5.3 from source :confused:

---

### Post by Reiger on 2009-12-20
[list="1"]
[*]You mean distribution of an all-you-can-eat + batteries-included pack? How about [XAMPP]("http://www.apachefriends.org/en/xampp.html")?
[*]It's probably possible with some dpkg parameters; alternatively compile PHP yourself and you get to choose where it will be installed...
[*]Because you install software from repositories which may or may not include the very latests of any given software. As for PHP it's 5.2, even in Lucid. (5.2.11)
[*]There's no gibberish there at all. This is typical for something large like PHP.
[/list]

Basically the commands do the following:
[list="1"]
[*]Install the Apache + required libraries to build PHP against Apache which enables you to use PHP with Apache.
[*]Install database server(s) + required libraries to build PHP so it can use these/this database server(s).
[*]Install a slew of libraries used by PHP to provide many functions such as compression, encryption (required for sessions amongst other thigns), image manipulation, URL wrappers in fopen() etc. etc... (last thing enables e.g. file_get_contents('http://www.google.com'); to get the HTML file at the [www.google.com](www.google.com) site.)
[*]Download & extract PHP source. Incidentally I would not advice doing this in ~ (aka your home directory, aka $HOME), rather I would first create a directory (mkdir) ~/php-src then do cd ~/php-src before downloading (wget) and extracting (tar). The tar -xvfz means &#8220;extract with verbose output the given file with gzip compression&#8221;.
[*]The configure step enables/disables various libraries, which corresponds to various modules/extensions in PHP. You can simply type ./configure and the script should prompt you for every option -- this &#8216;gibberish&#8217; specifies them right away so you are not prompted. This is mainly useful in automated compile & install scripts.
[*]Compile and install PHP from source.
[*]Step 7 edits necessary config files to instruct Apache where it can find your new PHP 5.3; and enables the module (a2enmod).
[/list]

EDIT: And you don't even have to build from source. You can enable some dotdeb repositories: [http://www.dotdeb.org/](http://www.dotdeb.org/)

---

### Post by aklo on 2009-12-20
Thanks i will definitely keep xampp on my to use list the next time.

Right now after much searching i installed LAMP already and was only wondering abou the 2 php versions. Ah well if it is too complicated then i always have my windows xp.

I'm doing some Joomla stuff on my windows xp partition and one of the plugin requires php5.2 which i now already have on my ubuntu, but personally for learning i would like to use php5.3 also.

---

