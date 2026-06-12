---
title: "/var/log/secure logfile parsing with perl script"
date: 2012-10-23
forum: Programming Talk
---

### Post by Habitual on 2012-10-23
Hello fellow coders:

This is NOT an Ubuntu-related post, so mods, please feel free to do what's needed. :)

I am trying to massage some data from /var/log/secure files on CentOS hosts using a local perl script. I grab the remote files locally.

I found this (sorta) recent [article]("http://catalog.codeproject.com/Articles/304421/Use-Perl-to-Summarize-the-Secure-Log-File-on-Linux") that discusses how to do it with perl, so I jumped in.

I have NO perl experience but I have managed to make some progress.
Please don't critique the code too badly, it didn't even work when I first ran it.
So what little data it does chew up and spit out I consider myself lucky for even that much.

It seems to not iterate over the $count and secure_out.log **always ***only shows one line* ```
FAILED root password from IP: 61.135.137.2
``` when that IP has banged on my boxes 100s of times.

```
grep 61.135.137.2 /home/jj/Documents/cirrhus9/c9archives/test.in | grep "Failed password for root" | wc -l
459
```I have no Perl skills but have managed what progress I have made without anything other than the O'Reilly "Programming Perl (4th Edition)" as a guide.  I am reading that while I wait for O'Reilly "Learning Perl (4th Edition)" to arrive at my local bookstore.

My "progress" is somewhat documented [here...]("http://www.linuxquestions.org/questions/programming-9/var-log-secure-parse-with-perl-script-guidance-needed-4175432516/#post4807236") (on another forum).
I didn't post that link for any other reason than to ask for help.

I am using perl v5.16.1
secure.pl script attached. Rename accordingly.
  
I am NOT interested in a perl one-liner.

Some sample data...```

Oct 16 13:55:12 domain.com sshd[21117]: Failed password for invalid user postgres from ::ffff:67.228.13.82 port 33738 ssh2
Oct 16 13:55:12 domain.com sshd[21125]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 33269 ssh2
Oct 16 13:55:13 domain.com sshd[21133]: Failed password for invalid user postgres from ::ffff:67.228.13.82 port 33746 ssh2
Oct 16 13:55:13 domain.com sshd[21141]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 33279 ssh2
Oct 16 13:55:14 domain.com sshd[21149]: Failed password for invalid user postgres from ::ffff:67.228.13.82 port 33894 ssh2
Oct 16 13:55:14 domain.com sshd[21153]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 33406 ssh2
Oct 16 13:55:15 domain.com sshd[21168]: Failed password for invalid user postgres from ::ffff:67.228.13.82 port 33965 ssh2
Oct 16 13:55:15 domain.com sshd[21169]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 33427 ssh2
Oct 16 13:55:15 domain.com sshd[21189]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 33475 ssh2
Oct 16 13:55:16 domain.com sshd[21188]: Failed password for invalid user postgres from ::ffff:67.228.13.82 port 34058 ssh2
Oct 16 13:55:16 domain.com sshd[21195]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 33494 ssh2
Oct 16 13:55:20 domain.com sshd[21205]: Failed password for invalid user postgres from ::ffff:67.228.13.82 port 34328 ssh2
Oct 16 13:55:20 domain.com sshd[21209]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 33670 ssh2
Oct 16 13:55:32 domain.com sshd[21221]: Failed password for invalid user postgres from ::ffff:67.228.13.82 port 35322 ssh2
Oct 16 13:55:34 domain.com sshd[21225]: Failed password for invalid user postgres from ::ffff:74.86.64.194 port 34595 ssh2
...
Oct 16 13:22:31 domain.com sshd[17227]: Failed password for root from ::ffff:217.18.242.235 port 46907 ssh2
Oct 16 13:22:32 domain.com sshd[17233]: Failed password for root from ::ffff:217.18.242.235 port 47025 ssh2
Oct 16 13:22:34 domain.com sshd[17241]: Failed password for root from ::ffff:217.18.242.235 port 47110 ssh2
Oct 16 13:22:35 domain.com sshd[17247]: Failed password for root from ::ffff:217.18.242.235 port 47293 ssh2
Oct 16 13:22:37 domain.com sshd[17253]: Failed password for root from ::ffff:217.18.242.235 port 47393 ssh2
Oct 16 13:22:38 domain.com sshd[17259]: Failed password for root from ::ffff:217.18.242.235 port 47554 ssh2
Oct 16 13:22:40 domain.com sshd[17265]: Failed password for root from ::ffff:217.18.242.235 port 47680 ssh2
Oct 16 13:22:41 domain.com sshd[17271]: Failed password for root from ::ffff:217.18.242.235 port 47832 ssh2
Oct 16 13:22:43 domain.com sshd[17277]: Failed password for root from ::ffff:217.18.242.235 port 47972 ssh2
Oct 16 13:22:45 domain.com sshd[17283]: Failed password for root from ::ffff:217.18.242.235 port 48144 ssh2
Oct 16 13:22:46 domain.com sshd[17289]: Failed password for root from ::ffff:217.18.242.235 port 48207 ssh2
...
Oct 16 09:24:02 domain.com sshd[17345]: Accepted publickey for root from ::ffff:142.255.102.34 port 46933 ssh2
Oct 16 13:24:02 domain.com sshd[17346]: Accepted publickey for root from ::ffff:142.255.102.34 port 36381 ssh2
Oct 16 09:24:02 domain.com sshd[17344]: Accepted publickey for root from ::ffff:142.255.102.34 port 36381 ssh2
Oct 16 09:28:49 domain.com sshd[17924]: Accepted publickey for root from ::ffff:74.86.203.42 port 56731 ssh2
Oct 16 13:28:49 domain.com sshd[17925]: Accepted publickey for root from ::ffff:74.86.203.42 port 56731 ssh2
Oct 16 14:19:51 domain.com sshd[22292]: Accepted publickey for root from ::ffff:24.101.150.38 port 48698 ssh2
Oct 16 10:19:51 domain.com sshd[22291]: Accepted publickey for root from ::ffff:24.101.150.38 port 48698 ssh2
Oct 16 14:20:33 domain.com sshd[22337]: Accepted publickey for root from ::ffff:24.101.150.38 port 48701 ssh2
Oct 16 10:20:33 domain.com sshd[22336]: Accepted publickey for root from ::ffff:24.101.150.38 port 48701 ssh2
Oct 16 14:20:51 domain.com sshd[22372]: Accepted publickey for root from ::ffff:24.101.150.38 port 48703 ssh2

```

Subscribed with interest.

Thank you for your time.

---

### Post by spjackson on 2012-10-23
I believe I've made the minimal changes to make it work. Revised version attached.

---

### Post by Habitual on 2012-10-23
> **spjackson said:**
> I believe I've made the minimal changes to make it work. Revised version attached.

Thank you ***very*** much.

works as I hoped.

Edit0: I KNEW it was "$badUserCount" :)

Edit1: I am verifying the results. Some counts seem to be "off".
nn.nnn.nnn.nn  attempted to login 7 times for my IP.

Progress is pending as I analyze the output....

$tomorrow{$*n*}++;
I suppose. 
Thanks for your time,

---

### Post by Habitual on 2012-10-26
Well, I am calling this Solved.
Here's what the script spits out...
```

Results of /var/log/secure scan:
          (Failed due to bad password: 301)
               Failed due to bad user: 149
                                     +______________
      Number of Failed Login Attempts: 450

     Number of Successful Root Logins: 510

Connection Details are:

    301 FAILED root passwords from IP: 199.168.141.102
      1 Invalid user r00t from IP: 199.168.141.102
      1 Invalid user test001 from IP: 31.171.241.38
      1 Invalid user test01 from IP: 31.171.241.38
      1 Invalid user test02 from IP: 31.171.241.38
      1 Invalid user test1 from IP: 31.171.241.38
      1 Invalid user test2 from IP: 31.171.241.38
    143 Invalid user test from IP: 31.171.241.38
      4 Successful Logins for root from IP: 209.156.244.98
     38 Successful Logins for root from IP: 24.101.150.38
    468 Successful Logins for root from IP: 74.86.203.42

Host Details are:
hostname
som.ipa.dre.ss

Report Date:
Oct-26-2012

```and here's the script:
```

#!/usr/bin/perl -W
# Written:    JJ of c9
# Purpose:    audit /var/log/secure on CentOS release 4.x
# Source :    http://www.codeproject.com/Articles/304421/Use-Perl-to-Summarize-the-Secure-Log-File-on-Linux
# Credits:  Steven Jackson - http://ubuntuforums.org/attachment.php?attachmentid=226005&d=1351026760
#        :    
# Edited :    Fri Oct 26, 2012 -  9:05:09 AM EDT
# Current:    rootonly.pl now processes the /root/.c9audit.log 'internally' 
#        :    using system("/bin/sort audit.log | /usr/bin/uniq -c"); 
    
my $dataFile = "/var/log/secure";
my $failedCount = 0;            # number of bad logins from any user
my $successCount = 0;           # number of successful logins from any user
my $badUserCount = 0;           # number of bad users
my $badPasswordCount = 0;       # number of bad passwords, excludes bad users
my %ips;
my %users;
my %successful;
my %failed;

open LOG, "<$dataFile";
open OUT, ">/root/.c9audit.log";

while (<LOG>) {
 $line = $_;
 next if ($line=~ /^\s*#/); # ignore comment lines
 if($line =~ /Failed password for root from .*?(\d+\.\d+\.\d+\.\d+)/)
  {
    print OUT "FAILED root passwords from IP: $1\n";
    if(exists $ips{$1})
    {
       $ips{$1}++;
    }
    else
    {
      $ips{$1} = 1;
    }
    if(exists $users{$1})
    {
      $users{$1}++;
    }
    else
    {
      $users{$1} = 1;
    }
    if(exists $failed{$1})
    {
      $failed{$1}++;
    }
    else
    {
      $failed{$1} = 1;
    }
    $failedCount++;
    $badPasswordCount++;
  }
  elsif($line =~ /Failed password for invalid user (.+) from .*?(\d+\.\d+\.\d+\.\d+)/)
  {
    print OUT "Invalid user $1 from IP: $2\n";
    if(exists $ips{$2})
    {
      $ips{$2}++;
    }
    else
    {
      $ips{$2} = 1;
    }
    if(exists $users{$1})
    {
      $users{$1}++;
    }
    else
    {
      $users{$1} = 1;
    }
    if(exists $failed{$1})
    {
      $failed{$1}++;
    }
    else
    {
      $failed{$1} = 1;
    }
    $failedCount++;
    $badUserCount++;
  }
  elsif($line=~ /Accepted password for (\w+) from .*?(\d*\.\d*\.\d*\.\d*)/ 
     || $line=~ /Accepted publickey for (\w+) from .*?(\d*\.\d*\.\d*\.\d*)/)
  {
    print OUT "Successful Logins for $1 from IP: $2\n";
    if(exists $ips{$2})
    {
      $ips{$2}++;
    }
    else
    {
      $ips{$2} = 1;
    }
    if(exists $users{$1})
    {
      $users{$1}++;
    }
    else
    {
      $users{$1} = 1;
    }
    if(exists $successful{$1})
    {
      $successful{$1}++;
    }
    else
    {
      $successful{$1} = 1;
    }
    $successCount++;
 }
}

print <<"END_OF_MESSAGE" ;
Results of /var/log/secure scan:
          (Failed due to bad password: $badPasswordCount)
               Failed due to bad user: $badUserCount
                                     +______________
      Number of Failed Login Attempts: $failedCount

     Number of Successful Root Logins: $successCount\n
Connection Details are:\n
END_OF_MESSAGE

system("/bin/sort /root/.c9audit.log | /usr/bin/uniq -c");
print "\n";
print "Host Details are:\n";
system("hostname");
$IP_eth1 = `ifconfig eth1`;
$IP_eth1 =~ s/.*inet addr:(.*)  Bcast:/1/;
print "" . $1 . "\n";
print "\n";
print "Report Date:\n";
system("date +%b-%e-%Y");
close LOG;
close OUT;
```It's my first "baby"!
Thanks to spjackson, whom I gave credit to [here...]("http://www.bournetoraiseshell.com/article.php/20121015194408743")

Thank you for your time,

Enjoy.

---

