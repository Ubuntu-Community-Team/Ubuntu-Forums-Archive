---
title: "Creating a Perl Script that Autoinstalls?"
date: 2008-08-22
forum: Programming Talk
---

### Post by terry123b99 on 2008-08-22
Hi,
The title may sound odd, but basically am looking into creating a Perl script that will install all the Ubuntu Codecs and a certain software when executed. My need for this is due to the fact I manage over 80 Ubuntu systems and wish to have a Perl program I can execute on each machine that will install certain software.

For example, it will install (using apt-get) all the various codecs (mp3/divx..etc).

I have created a very simple, I mean very simple script that calls another file (install.sh). I would prefer the one perl script to do it all for me. The question is how do I get Perl to use apt get to do this?

Hope you understand lol

Regards,
Terry

---

### Post by scragar on 2008-08-22
```
#!/usr/bin/perl

$output = `gksu apt-get -y install whatever`;

print "apt-get installed some stuff, it said:\n$output";
```

---

### Post by ghostdog74 on 2008-08-22
why don't you download all the software you needed first? then install on all your servers.?

---

### Post by slavik on 2008-08-22
or set up your repo with your own meta-package that requires the packages you want.

then you can do (rough idea):
ssh systemname 'apt-get install packagename'

---

### Post by terry123b99 on 2008-08-23
> **scragar said:**
> ```
#!/usr/bin/perl

$output = `gksu apt-get -y install whatever`;

print "apt-get installed some stuff, it said:\n$output";
```

Thanks just what I was looking for, am now thinking of creating a simple user selection system wereas if the user presses (lets say the number 1) it will install codec or if user presses number 2 it will install somthing else? any ideas for a good piece of code to do this?

---

### Post by scragar on 2008-08-23
> **terry123b99 said:**
> Thanks just what I was looking for, am now thinking of creating a simple user selection system wereas if the user presses (lets say the number 1) it will install codec or if user presses number 2 it will install somthing else? any ideas for a good piece of code to do this?

```
#!/usr/bin/perl

use Switch;

my $got = '';

while($got ne 'q' and $got ne 'Q'){
  switch ($val) {
    case '1'{
      # here you install a codec.
    }
    case '2'{
      # something else
    }
  }
  print "\e[H\e[J";# clears the screen, don't use if you don't want.
                   # personally I say go for it
  print "1 - install codec\n";
  print "2 - something else\n";
  $got = getone();
}

### this is the end of the bit of the file you should edit, unless you know what your doing anyway

exit;
BEGIN {
  use POSIX qw(:termios_h);
  my ($term, $oterm, $echo, $noecho, $fd_stdin);
  $fd_stdin = fileno(STDIN);
  $term     = POSIX::Termios->new();
  $term->getattr($fd_stdin);
  $oterm     = $term->getlflag();
  $echo     = ECHO | ECHOK | ICANON;
  $noecho   = $oterm & ~$echo;
  sub cbreak {
    $term->setlflag($noecho);
    $term->setcc(VTIME, 1);
    $term->setattr($fd_stdin, TCSANOW);
  }
  sub cooked {
    $term->setlflag($oterm);
    $term->setcc(VTIME, 0);
    $term->setattr($fd_stdin, TCSANOW);
 }
 sub getone {
   my $key = '';
   cbreak();
   sysread(STDIN, $key, 3);
   cooked();
   return $key;
 }
}
END{
  cooked()
}
```

---

### Post by slavik on 2008-08-23
why not use curses???

---

### Post by terry123b99 on 2008-08-23
```

while($got ne 'q' and $got ne 'Q'){
  switch ($val) {
    case '1'{
      # here you install a codec.
    }
    case 2{
      # something else
    }
  }
  print "\e[H\e[J";# clears the screen, don't use if you don't want.
                   # personally I say go for it
  print "1 - install codec\n";
  print "2 - something else\n";
  $got = getone();
}

```

Keep getting errors here, is case 2 supposed to be case '2'?

---

### Post by scragar on 2008-08-23
yes, it should be.



Oh, forgot to include switch:
```

#!/usr/bin/perl

**use Switch;**

my $got = '';
```

---

### Post by terry123b99 on 2008-08-23
```

my $got = '';
while($got ne 'q' and $got ne 'Q'){
  switch ($val) {
    case '1'{
      print "option 1 selected"
    }
    case '2'{
      print "option 2 selected"
    }
  }
  print "\e[H\e[J";# clears the screen, don't use if you don't want.
                   # personally I say go for it
  print "1 - install codec\n";
  print "2 - something else\n";
  $got = getone();
}

```

This is the actal code am using to test it, and this is the error:

```

Unquoted string "case" may clash with future reserved word at ubuntuinstaller.pl line 20.
String found where operator expected at ubuntuinstaller.pl line 20, near "case '1'"
	(Do you need to predeclare case?)
Unquoted string "case" may clash with future reserved word at ubuntuinstaller.pl line 23.
String found where operator expected at ubuntuinstaller.pl line 23, near "case '2'"
	(Do you need to predeclare case?)
syntax error at ubuntuinstaller.pl line 19, near ") {"
syntax error at ubuntuinstaller.pl line 23, near "case '2'"
Execution of ubuntuinstaller.pl aborted due to compilation errors.

```

any ideas, am fairly new to perl as you can probably guess :)

thanks in advance

---

### Post by scragar on 2008-08-23
see my edits, I forgot to include the switch library :P

---

### Post by terry123b99 on 2008-08-23
great thanks, no errors anymore but think am going wrong somewhere. the menu appears fine, but when a number is selected nothing happens.

```

use Switch;

my $got = '';

while($got ne 'q' and $got ne 'Q'){
  switch ($val) {
    case '1'{
      print 'gksu apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar'
    }
    case '2'{
      print 'option 2 selected'
    }
  }
  print "\e[H\e[J";# clears the screen, don't use if you don't want.
                   # personally I say go for it
  print "##################################################################\n";
  print "################ TERRYS UBUNTU AUTOINSTALLER #####################\n";
  print "##################################################################\n";
  print "1 - Install essential codecs\n";
  print "2 - Coming Soon....\n";
  $got = getone();
}

```

---

### Post by ghostdog74 on 2008-08-23
> **terry123b99 said:**
> great thanks, no errors anymore but think am going wrong somewhere. the menu appears fine, but when a number is selected nothing happens.

```

use Switch;

my $got = '';

while($got ne 'q' and $got ne 'Q'){
  switch ($val) {
    case '1'{
      print 'gksu apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar'
    }
    case '2'{
      print 'option 2 selected'
    }
  }
  print "\e[H\e[J";# clears the screen, don't use if you don't want.
                   # personally I say go for it
  print "##################################################################\n";
  print "################ TERRYS UBUNTU AUTOINSTALLER #####################\n";
  print "##################################################################\n";
  print "1 - Install essential codecs\n";
  print "2 - Coming Soon....\n";
  $got = getone();
}

```

from where did you get $val?

---

### Post by scragar on 2008-08-23
comment out the line that clears the screen(it's get comments after it).

---

### Post by scragar on 2008-08-23
> **ghostdog74 said:**
> from where did you get $val?

erm yeah, sorry, copy and pasting 2 files together :P

it should read $got

---

### Post by scragar on 2008-08-23
> **terry123b99 said:**
> great thanks, no errors anymore but think am going wrong somewhere. the menu appears fine, but when a number is selected nothing happens.

```

use Switch;

my $got = '';

while($got ne 'q' and $got ne 'Q'){
  switch ($val) {
    case '1'{
      print **'**gksu apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar**'**;
    }
    case '2'{
      print 'option 2 selected';
    }
  }
#  print "\e[H\e[J";# clears the screen, don't use if you don't want.
                    # personally I say go for it
  print "##################################################################\n";
  print "################ TERRYS UBUNTU AUTOINSTALLER #####################\n";
  print "##################################################################\n";
  print "1 - Install essential codecs\n";
  print "2 - Coming Soon....\n";
  $got = getone();
}

```

quick point, to execute the command you don't use single quotes, you use the funny quote marker above tab(under escape):```
      print **`**gksu apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar**`**;

```

Oh, and try to end lines with commands on with a semi colon( ; ), it's not always required, but while there's nothing lost for adding it you can throw errors if you forget it.

---

