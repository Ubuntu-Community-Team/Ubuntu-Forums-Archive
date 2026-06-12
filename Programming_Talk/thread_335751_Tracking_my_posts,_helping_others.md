---
title: "Tracking my posts, helping others"
date: 2007-01-10
forum: Programming Talk
---

### Post by phossal on 2007-01-10
I joined the forums because I wanted to give back to the community that had helped me get up and running. I appreciate good, concise information delivered promptly. tseliot is the king of it, in my opinion. The guy posts meaningful, lean content, and he does it fast.

I wanted to carefully pick and choose the people I responded to. I pick people who are having troubles with things I have a good understanding of: the wg111v2, java/eclipse/tomcat, and bash among other things. Quickly, though, I realized it was *difficult* to find out if someone I was helping had responded to me. I had no idea which posts I needed to get back to. Even using Search>Find All Your Posts only gave me a list of the things I was involved in. It lists the total responses, but I can't remember the totals over the course of a couple hours, let alone a couple days.

So, to help myself help others, I wrote a perl script. It's down and dirty, but does the job. Now I go to Search>Find All Your Posts, ctrl-s, and save search.php to my desktop. 

I run the perl script, and then I *help people*. I know some of you are even more committed (and probably should be, in another sense :D  ) than I am, so I'm sharing:

[edit] Since I know at least one of you will post a much better, 5-line *Python* version of this program, I *will* start using yours as soon as it's available. :)


```
#!/usr/bin/perl

#This is a short program to see if any replies have hit my posts.
#It will simply parse the data I give it and compare it to the stored numbers.


#Variables
$storage = '/home/<user>/Desktop/Ubuntu Forums/storage.txt';
$file =  "/home/<user>/Desktop/search.php";



#open the last stored file
%posts = (); #Create the hash, and load it.

open (SNF, $storage) or die "Cannot read storage file\n";
@rsi = <SNF>;

#For every entry in the file, load the hash.
for (@rsi) {
	if ($_ =~ /(.*):!!:(.*)/) {
		$posts{$1} = $2;
	}
}




#open the posts file.
open (INF, $file) or die "Cannot open file!";
@contents = <INF>;
close (INF);

#See if any posts have been made
for (@contents) {

	#Search Keys
	$post =  'a href="showthread.php?p';
	$s1 = '<strong>';
	$s2 = '</strong>';



	#Get # of replies
	if ($_ =~ /Replies.*$s1(.*)$s2/) {
		$r = $1;
	}

	#Get Topic
	if ($_ =~ /$post.*$s1(.*)$s2/) {
		$t = $1;
		if ($posts{$t}) { #if the topic is defined in the hash... 
			if ($posts{$t} < $r) { #...check to see if the replies have gone up.
				print "Updated: $t\n";
				$posts{$t} = $r;
			}
		} else { #If the topic isn't defined in the hash, define it.
			$posts{$t} = $r; 
			print "New Topic: $t\n";
		}	

	}

	

}



#write the storage file
open (OUF, ">".$storage) or die "Cannot open file for writing\n";

while( my ($k, $v) = each %posts ) {
	print OUF "$k:!!:$v\n";
}

close OUF;

unlink($file);

```

---

### Post by Tomosaur on 2007-01-10
Uhh. There's already a subscription feature :S

---

### Post by phossal on 2007-01-10
lol A what?

---

### Post by Lord Illidan on 2007-01-10
> **Tomosaur said:**
> Uhh. There's already a subscription feature :S

aye, why bother with this, when you can just check your e-mail?

---

### Post by phossal on 2007-01-10
*Email?!* No Ubuntu stuff goes to my *actual* email, and the only site email I get are notifications of being banned.

---

### Post by Tomosaur on 2007-01-10
> **phossal said:**
> *Email?!* No Ubuntu stuff goes to my *actual* email, and the only site email I get are notifications of being banned.

Just create an ubuntu folder and forward all ubuntuforums stuff into that. You can subscribe to threads using the thread tools button.

---

### Post by eteran on 2007-01-11
If you dont like the email notifications, you can also do an advanced search, look for your exact username, leave all the other options on default. 
Will show all the Threads you have been posted in, with the newest replies on top. You can even bookmark this page.

---

### Post by Wybiral on 2007-01-11
Maybe he/she would rather write something to accomplish it... There's nothing wrong with a programmer wanting to program something for use with the programming boards, is there?

---

### Post by Mirrorball on 2007-01-11
Turn on automatic subscription for all threads you participate in, with *no* email notification. Then go to Quick Links -> Subscribed Threads: list of threads you participated in. ;)

---

