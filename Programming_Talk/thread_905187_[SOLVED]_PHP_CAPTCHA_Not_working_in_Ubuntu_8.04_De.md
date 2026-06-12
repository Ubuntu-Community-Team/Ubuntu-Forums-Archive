---
title: "[SOLVED] PHP CAPTCHA Not working in Ubuntu 8.04 Desktop"
date: 2008-08-30
forum: Programming Talk
---

### Post by ivikas on 2008-08-30
Hello all,

         I have an ubuntu 8.04 desktop and i have a lamp on it.Iam using php5 and now i have to use CAPTCHA for my local web development.I searched and found that for using CAPTCHA i need to install php5-gd.Is this library neccessary for all image uploading,image gallary creation?? I installed php5-gd but still CAPTCHA is not working.During installation of php5-gd one package was set to remove,this is as below

-----------------------------------------------------------------------
Reading package lists... Done
Building dependency tree       [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libgtk1.2 libsoup2.2-8 xulrunner-1.9-dom-inspector devhelp-common python-libgmail libzvbi-common libgbf-1-common libgtk1.2-common python-fuse
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgd2-xpm libt1-5
Suggested packages:
  libgd-tools
[COLOR="Red"]The following packages will be REMOVED:
  libgd2-noxpm
[/COLOR]The following NEW packages will be installed:
  libgd2-xpm libt1-5 php5-gd
0 upgraded, 3 newly installed, 1 to remove and 248 not upgraded.
Need to get 491kB of archives.
After this operation, 512kB of additional disk space will be used.
Do you want to continue [Y/n]? y
---------------------------------------------------------------------
Is there any problem with this removal
I first stopped apache2 webserver,then installed  php5-gd with 

apt-get install php5-gd

After this i have even restarted apache2 and cleared firefox cache and reloaded my php page containing CAPTCHA.

I also checked the phpinfo();

The output of phpinfo();
---------------------------------------------------------------------
GD Support 	      enabled
GD Version 	      2.0 or higher
FreeType Support      enabled
FreeType Linkage      with freetype
FreeType Version      2.3.5
T1Lib Support 	      enabled
GIF Read Support      enabled
GIF Create Support    enabled
JPG Support 	      enabled
PNG Support 	      enabled
WBMP Support 	      enabled
-----------------------------------------------------------------------

It says GD is enabled.But still my CAPTCHA is nor working...Can anyone give a fix.

Thanks in advance:guitar:

---

### Post by gmxgeek on 2008-08-30
can you go to the actual CAPTCHA script itself in web browser and see what it says?

if it says something about a font, make sure that the font is in the same dir, and it is readable and executable. you might have to change the path to the file in the script to ./filename.ttf instead of filename.ttf

---

### Post by ivikas on 2008-08-30
I have a registeration form and in it there is a place for captcha,but the captcha image is not all displayed.No font froblem as i have font on the system.
Can you tell me where is wrong.I have now run a windows developed php project into ubuntu.The captch image section is not at all displayed.Is there any way to get around or is ubuntu 8.04 does have a minimal support or no support at all.

---

### Post by gmxgeek on 2008-08-30
there should be an actual script that is called captcha.php or something that your form is linking into. please go to that address, or simply post the url of the page in question and I'll try to track it down

it sounds like permission errors or location error that i used to get all the time with captchas

---

### Post by ivikas on 2008-08-30
This script [COLOR="Red"]CaptchaSecurityImages.php [/COLOR] generates the php image and
below is how i linked it in my registration form.This is the captcha iam using

[http://www.white-hat-web-design.co.uk/articles/php-captcha.php](http://www.white-hat-web-design.co.uk/articles/php-captcha.php)

I have removed the html tag(<,>, at begining and end of img tag) below just for displaying it in this forum,so don't consider this as a mistake.


img src="CaptchaSecurityImages.php?width=100&height=40&characters=5" align="absmiddle"

---

### Post by gmxgeek on 2008-08-30
> **ivikas said:**
> This script [COLOR="Red"]CaptchaSecurityImages.php [/COLOR] generates the php image and
below is how i linked it in my registration form.This is the captcha iam using

[http://www.white-hat-web-design.co.uk/articles/php-captcha.php](http://www.white-hat-web-design.co.uk/articles/php-captcha.php)

I have removed the html tag below just for displaying it in this forum,so don't consider this as a mistake.


img src="CaptchaSecurityImages.php?width=100&height=40&characters=5" align="absmiddle"

okay, it looks like the same script i use.
go to CaptchaSecurityImages.php in your browser, and it should give you an error. Copy and paste for me please.

Is this a local server?

and try opening that script, changeing the $fontpath = 'monospace.ttf' to './monospace.ttf'

i don't remember exactly what it says, i am very tired. So good luck!

---

### Post by ivikas on 2008-08-30
Hello gmxgeek,

             First of all a very hearty thanks for your patience and helping mentality.
I run the script CaptchaSecurityImages.php directly in the browser and it output the following error

Warning: imagettfbbox() [function.imagettfbbox]: Could not find/open font in /var/www/oneworld/CaptchaSecurityImages.php on line 60
Error in imagettfbbox function

Once more thanks for your patience.

---

### Post by ivikas on 2008-08-30
Hello gmxgeek,

I have done as what you said like the following in CaptchaSecurityImages.php script

                        var $font = './monofont.ttf';

and it's WORKING.Thanks a lot for your effort and patience.

Thanks dude

---

### Post by Reiger on 2008-08-30
Also certain Captcha's don't work properly with Firefox right away; requiring a reload of the image.

---

### Post by gmxgeek on 2008-08-30
> **Reiger said:**
> Also certain Captcha's don't work properly with Firefox right away; requiring a reload of the image.

```

$PathToScript = "/path/to/captcha.php";
print "<img src=\"$PathToScript\" alt=\"Error Creating Security Code\" ";
print "onClick=\"this.src += this.src.match(/hires/) ? '.' : '&amp';\">";
print "<span>(Click for another)</span>";

```

That will allow another captcha to load when the user clicks on it.

Replace $PathToScript with the valid script path, including parameters

---

