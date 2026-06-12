---
title: "Perl script to alphabetize desktop icons on Xubunut"
date: 2007-02-15
forum: Programming Talk
---

### Post by BrendanM on 2007-02-15
So I'm trying to teach myself Perl, and I was also unable to find any way to automatically sort/organize the desktop icons on Xubuntu, so I wrote this script to do it. It arranges all the icons alphabetically along the lefthand side of the desktop. It also cleans up the icons.screen0.rc file and removes unneeded entries (for some reason Xfce seems to leave entries for every icon you've ever had, even after you delete them). After you run the script, you have to either press F5 or log out and back in to refresh the desktop.

I hope some other Xubuntu users with cluttered desktops get some use out of it. This is the first thing I've ever written in Perl; if any Perl hackers out there have tips/suggestions, I'd love to hear them.

---

### Post by LotsOfPhil on 2007-02-16
In this part:
```

$test = substr($raw_data[$i],0,1);
	if ($test eq "[") {
		$icons[$c] = $raw_data[$i];
		$c++;
	}

```
You can get rid of the variable $test by just having:
```

	if (substr($raw_data[$i],0,1) eq "[") {
		$icons[$c] = $raw_data[$i];
		$c++;
	}

```

Also, you can change the 
```

if ($c == 1){
		$final[$k] = $sorted_icons[$i];
		$k++;
		}

```
to
```

if ($c){
		$final[$k] = $sorted_icons[$i];
		$k++;
		}

```
0 is false, anything else is true.

---

### Post by BrendanM on 2007-02-18
Cool, thanks for the tips.

---

### Post by nLinked on 2011-08-12
> **BrendanM said:**
> So I'm trying to teach myself Perl, and I was also unable to find any way to automatically sort/organize the desktop icons on Xubuntu, so I wrote this script to do it. It arranges all the icons alphabetically along the lefthand side of the desktop. It also cleans up the icons.screen0.rc file and removes unneeded entries (for some reason Xfce seems to leave entries for every icon you've ever had, even after you delete them). After you run the script, you have to either press F5 or log out and back in to refresh the desktop.

I hope some other Xubuntu users with cluttered desktops get some use out of it. This is the first thing I've ever written in Perl; if any Perl hackers out there have tips/suggestions, I'd love to hear them.

This is great, but is there any way to also tell it to refresh the desktop for you?

---

### Post by BrendanM on 2011-08-15
Wow, I'm surprised and pleased that more than 5 years later somebody would find this old script. I hope it was helpful.

I still don't know Perl properly, but I did some research and it looks like "xfdesktop --reload" should refresh the Xfce desktop. I've added an exec line to the end of this script accordingly.

Please note that this was originally written for Xfce 4.4, and I believe Xfce is on 4.8 now, so it might not work exactly as expected anymore. These days, I'm running standard Ubuntu so I don't have a system to test it on.

---

### Post by hwttdz on 2011-10-19
Here's one that does folders before files and hides files starting with . or ending in ~ (well really hides files that end in ~ or that have '/.' anywhere in the file name).

```
use strict;

my $max_row = 8;
my $row = 0;
my $col = 0;
my $home = $ENV{'HOME'};

my @icons_to_hide = `find ~/Desktop -mindepth 1 -maxdepth 1 -type f|grep '~'|sort`;
chomp(@icons_to_hide);
for(my $icon=0; $icon < scalar(@icons_to_hide); $icon++)
{
	my $curr_icon = @icons_to_hide[$icon];
	my $new_icon = $curr_icon;
	$new_icon =~ s/(.*)\/(.*)~/$1\/.$2/; # cut off up until last slash
	system("mv $curr_icon $new_icon");
}

# first list desktop directories in order
my @desktop_icons = `find ~/Desktop -mindepth 1 -maxdepth 1 -type d|sort`;

# then list desktop files in order, omit backups
push(@desktop_icons,`find ~/Desktop -mindepth 1 -maxdepth 1 -type f|grep -Ev '\/\\\.'|sort`);

my $outfile = "$home/.config/xfce4/desktop/icons.screen0.rc";
open(my $outfilehandle, ">", "$outfile") or die "Could not open $outfile:\n$!"; #open for write, overwrite
chomp(@desktop_icons);
for(my $icon=0; $icon < scalar(@desktop_icons); $icon++)
{
	my $curr_icon = @desktop_icons[$icon];
#	system("touch $curr_icon");
	$curr_icon =~ s/.*\///; # cut off up until last slash
	print $outfilehandle "[$curr_icon]\n";
	print $outfilehandle "row=$row\n";
	print $outfilehandle "col=$col\n";
	print $outfilehandle "\n";
	$row++;
	if($row > $max_row)
	{
		$row = 0;
		$col++;
	}
}

close $outfilehandle;
#system("cat $outfile");
system("touch $outfile");
system("xfdesktop --reload");
```

---

