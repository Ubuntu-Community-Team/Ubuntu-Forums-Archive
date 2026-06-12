---
title: "while vs. until usage in script help"
date: 2013-07-31
forum: Programming Talk
---

### Post by Habitual on 2013-07-31
I've posted this in a couple of places, but I need help with it still.

This script I mashed together and it needs a 'nudge' as it doesn't do what I intended.

It works for the most part, it just doesn't delete the previous days' archive **as intended**. Funny how that "works" :)

```
!/bin/bash
#07/30/2013 09:24:52 AM EDT
export TERM=linux
export EC2_HOME=/home/c9admin/ec2/ec2-api-tools/current # ec2-api-tools-1.6.7.2
export PATH=$PATH:$EC2_HOME/bin
export JAVA_HOME=/usr
export AWS_ACCESS_KEY=
export AWS_SECRET_KEY=
export EC2_URL=https://ec2.us-west-2.amazonaws.com

ec2-copy-image -r us-east-1 --region us-west-2 -s $(sed -n '1p' /home/c9admin/dwd/dataworks.lst | awk '{print $2}') -n $(date '+%m%d%Y')_sftpserver -d "Daily Dataworks backup"
OLD_IMAGE=$(ec2-describe-images | grep "ami-" | grep $(date +"%m%d%Y" --date="1 days ago")_dataworks | awk '{print $2}')
OLD_SNAPS=$(ec2-describe-images $OLD_IMAGE | grep snap | awk '{print $4}')

DE_REGISTER()
{
for i in $OLD_IMAGE
         do ec2-deregister "$i"
done
}

DEL_SNAPSHOTS()
{
for i in $OLD_SNAPS
        do ec2-delete-snapshot "$i"
done
}

# Edited 07/30/2013 09:23:09 AM EDT
while RESULT=$(ec2-describe-images --filter state=pending | grep $(date +"%m%d%Y")_dataworks)
do
sleep 1m
done
DE_REGISTER
DEL_SNAPSHOTS
exit 0
#EOF
```

What I intended  for it to "do" is wait until the Image State becomes "Available" before deleting yesterday's archive using these 2 functions:
DE_REGISTER 
DEL_SNAPSHOTS

The script runs and does create the archive, just no deleting takes place.

Sample Output:
```
IMAGE    ami-36f48e5f    012345678901/07312013_dataworks    012345678901    available    private        x86_64    machine        windows    ebs    hvm    xen
IMAGE    ami-36f48e5f    012345678901/07312013_dataworks    012345678901     pending    private        x86_64    machine        windows    ebs     hvm    xen
```

I believe I need to use this until statement instead of while:
```
until RESULT=$(ec2-describe-images --filter state=available | grep $(date +"%m%d%Y")_dataworks);  
do
sleep 1m
done
DE_REGISTER
DEL_SNAPSHOTS
exit 0
#EOF
```

I've already modified the script so we'll know for sure tomorrow morning, but still, I could use an experienced review of the logic.

I encourage and value your replies.
Thank you for your time

---

### Post by Vaphell on 2013-08-02
*until* should work, as should *while ! RESULT=$( ... )*


you unnecessarily use grep+awk or sed+awk given that awk can filter on its own
eg
```
OLD_IMAGE=$(ec2-describe-images | grep "ami-" | grep $(date +"%m%d%Y" --date="1 days ago")_dataworks | awk '{print $2}')
OLD_IMAGE=$( ec2-describe-images | awk -vd=$(date +%m%d%Y -d 'yesterday') '$2~"ami-" && $3~d { print $2; }' )  

OLD_SNAPS=$(ec2-describe-images $OLD_IMAGE | grep snap | awk '{print $4}')
OLD_SNAPS=$(ec2-describe-images "$OLD_IMAGE" | awk '/snap/{print $4}')

ec2-copy-image -r us-east-1 --region us-west-2 -s $(sed -n '1p' /home/c9admin/dwd/dataworks.lst | awk '{print $2}') -n $(date '+%m%d%Y')_sftpserver -d "Daily Dataworks backup"
ec2-copy-image -r us-east-1 --region us-west-2 -s $( awk 'NR==1 {print $2}' /home/c9admin/dwd/dataworks.lst ) -n $(date '+%m%d%Y')_sftpserver -d "Daily Dataworks backup"

```

---

### Post by Habitual on 2013-08-02
Vaphell:

I knew changing the subject would get your attention.

Yes, I know my use of grep+awk is a bit "amateurish".

Thanks for cleaning that up for me.

I also notice that I now have 2 less variable assignments also.

AMIDATE=
SFTPSERVER_AMI_SOURCE=

Is there a technical reason for the use of spaces around the use of  ```
$( awk 'NR==1 {print $2}' /home/c9admin/dwd/sftpserver.lst )
```?
I know the script I posted showed /home/c9admin/dwd/dataworks.lst, but that was an error.

Thank you very much.

Edit: Fri Aug 02, 2013 - 9:33:13 AM EDT

Here's the corrected code snippets:
```
#OLD_IMAGE=$(ec2-describe-images | grep "ami-" | grep $(date +"%m%d%Y" --date="1 days ago")_sftpserver" | awk '{print $2}')
OLD_IMAGE=$( ec2-describe-images | awk -vd=$(date +%m%d%Y)_sftpserver '$2~"ami-" && $3~d { print $2; }' )  

#OLD_SNAPS=$(ec2-describe-images $OLD_IMAGE | grep snap | awk '{print $4}')
OLD_SNAPS=$(ec2-describe-images "$OLD_IMAGE" | awk '/snap/{print $4}'sftpserver")

#ec2-copy-image -r us-east-1 --region us-west-2 -s $(sed -n '1p'  /home/c9admin/dwd/sftpserver.lst | awk '{print $2}') -n $(date  '+%m%d%Y')_sftpserver -d "Daily Dataworks backup"
ec2-copy-image -r us-east-1 --region us-west-2 -s $( awk 'NR==1 {print  $2}' /home/c9admin/dwd/sftpserver.lst  ) -n $(date '+%m%d%Y')_sftpserver  -d "Daily sftpserver backup"

```

I changed your suggestion on
```
OLD_IMAGE=$( ec2-describe-images | awk -vd=$(date +%m%d%Y -d 'yesterday') '$2~"ami-" && $3~d { print $2; }' )
```
to
```
 OLD_IMAGE=$( ec2-describe-images | awk -vd=$(date +%m%d%Y -d 'yesterday')_sftpserver '$2~"ami-" && $3~d { print $2; }' ) 
```
that further isolates the correct target, as this script runs in triplicate for 3 separate servers.

You are a SuperStar, Thank you!

---

### Post by Vaphell on 2013-08-02
> Is there a technical reason for the use of spaces around the use of
Code:

$( awk 'NR==1 {print $2}' /home/c9admin/dwd/sftpserver.lst )

?

no, while bash sometimes is space-sensitive, in case of $() it doesn't matter. Spaces are my subjective preference - i find the code more readable :)

---

### Post by Habitual on 2013-08-02
Thanks!

---

### Post by Habitual on 2013-08-04
This morning I woke up early at 2AM and saw that the very script I had used for this post had deleted *all the images* in us-west-2.
Ouch.

NBD.


Not wishing to jeopardize any more of my Client's resources, I just removed the  everything below
```
ec2-copy-image -r us-east-1 --region us-west-2 -s $( awk 'NR==1 {print $2}' /home/c9admin/dwd/sftpserver.lst ) -n $(date '+%m%d%Y')_sftpserver -d "Daily sftpserver backup"
```
and I'll delete them by hand until I can get a grip on this later.

I use a "delete" script for the cleanup of yesterday's archives and schedule that for like 12 hours after the AMIs get copied to the new region.

I notice that 
```
awk 'NR==1 {print $2}' /home/c9admin/dwd/sftpserver.lst 
```
and
```
awk '{print $2}' /home/c9admin/dwd/sftpserver.lst
```
produce the same result. Curious about the "NR==1". so I have some homework.

Comments encouraged.

Thank you,

---

### Post by Vaphell on 2013-08-05
sorry about unforeseen consequences, i must say putting untested scripts in production requires balls ;-)
you should run the script for few days with destructive commands commented out and dump the debug info to some file to see if proper code paths are hit.

NR is simply Record Number. Records in awk are by default lines (record separator RS is set to newline but can be modified)
NR==1 asks for 1st row only, just like sed -n 1p (print only 1st line) which i believe was used previously for that purpose
first tree rows? NR<=3 or NR<4. Rows between 10 and 20? NR>=10 && NR<=20 or NR>9 && NR<21, etc etc.

```
$ echo $'1 2 3\na b c'
1 2 3
a b c
$ echo $'1 2 3\na b c' | awk '{ print $2 }'
2
b
$ echo $'1 2 3\na b c' | sed -n 1p | awk '{ print $2 }'
2
$ echo $'1 2 3\na b c' | awk 'NR==1 { print $2 }'
2
```

---

### Post by Habitual on 2013-08-05
> **Vaphell said:**
> sorry about unforeseen consequences, i must say putting untested scripts in production requires balls ;-)
Yeah, I move way too fast sometimes.

[QUOTE=]you should run the script for few days with destructive commands commented out and dump the debug info to some file to see if proper code paths are hit.[/QUOTE]
I was thinking along the lines of "echo (destructive...) > /path/to/file.err?

[QUOTE=]
NR is simply Record Number. Records in awk are by default lines (record separator RS is set to newline but can be modified)
NR==1 asks for 1st row only, just like sed -n 1p (print only 1st line) which i believe was used previously for that purpose
first tree rows? NR<=3 or NR<4. Rows between 10 and 20? NR>=10 && NR<=20 or NR>9 && NR<21, etc etc.[/QUOTE]

Thanks for the summary usage and explanation, I appreciate that and I **still** will do my due diligence.
I hate my usage of grep | awk | cut, it's terribly inefficient. And I admit, I haven't studied awk at all.
20 Years in IT and I still code sometimes like a noob.

How would *you* handle the destructive routine?
I'm not asking for a solution, just maybe a routine or procedure I haven't thought of...

Thank you for your time.
It is not lost on me.

---

### Post by Vaphell on 2013-08-05
of course echoing out *rm*s and *mv*s and such, just like you said. Usually i put destructive stuff as the very last thing. My WIP scripts are full of echos and printfs printing anything that matters so i can easily pinpoint the moment in which they go off tracks.

i'd also think about creating a fake enviromnent mimicking the real thing and running the script in it, losing few dummy files is not a problem. If needed i'd substitute ec2-* programs with fixed outputs for the time being, so it's easy to test specific scenarios and manufacture border cases that are rare in the wild. 


yes, awk is well worth it but like with everything there is a non-zero barrier of entry. If you have a one time task, most likely you will whip up something of things you already know, not learn a new tool.
If you have to work with text beyond standard sed s///, awk is your friend. It's tailored for text, has variables, arrays, logic operators and whatnot which make things borderline impossible in sed a breeze.
Granted, it's a bit more verbose than sed incantations but verbosity is not a bad thing if it comes with clarity.

---

### Post by Habitual on 2013-08-05
Vaphell:

At what point does it become "beneficial" to assign variables in such a 'simple' script?
If I go the in-line route using
```
ec2-deregister $(ec2-describe-images | awk -vd=$(date +%m%d%Y -d 'yesterday')_dataworks '$2~"ami-" && $3~d { print $2; }')
```

I can get this down to 2 lines of destructive statements *and* remove 2 more variable assignments, but I don't like 
```
OLD_SNAPS=$(ec2-describe-images $OLD_IMAGE | grep snap | awk '{print $4}')
```

looks like the "old" JJ ;)

```
ec2-describe-images $OLD_IMAGE
IMAGE    ami-0f37a53f    012345678901/08042013_dataworks    012345678901    available    private        x86_64    machine        windows    ebs    hvm    xen
BLOCKDEVICEMAPPING    EBS    /dev/sda1        snap-8c98d0b6        false    standard    
BLOCKDEVICEMAPPING    EBS    xvdi        snap-8398d0b9        false    standard    
BLOCKDEVICEMAPPING    EBS    xvdh        snap-8698d0bc        false    standard    
BLOCKDEVICEMAPPING    EBS    xvdm        snap-8598d0bf        false    io1    4000
BLOCKDEVICEMAPPING    EPHEMERAL    /dev/xvdf    ephemeral0
BLOCKDEVICEMAPPING    EPHEMERAL    /dev/xvdg    ephemeral1
```

can you help me out with an awk variable assignment for that output?
Just the snap- lines.

Thanks. 
So close!

---

### Post by Vaphell on 2013-08-06
```
awk '/snap/ { print $4 }'
```
or to be more specific
```
awk '$4~/snap/ { print $4 }'
```

as to when to use variables to substitute commands.... imo it comes to intuition, when the code becomes an unreadable mess that is hard to comprehend at a glance
eg in case of ```
ec2-describe-images | awk -vd=$(date +%m%d%Y)_sftpserver '$2~"ami-" && $3~d { print $2; }'
```
it would be ok to roll date+server into a variable so it doesn't add good 30% to the line length.
```
tmp=$(date +%m%d%Y -d yesterday )_sftpserver
ec2-describe-images | awk -vd="$tmp" '$2~/ami-/ && $3~d { print $2; }'
```
it's obvious that you want $3 to match some supplied pattern, while the inlined version obfuscates the main idea a bit as you have to read deeper to get what's going on here.

inlining everything makes script much harder to debug. When you have an array or a variable  you can print contents as soon as something starts smelling funny. Inlined code needs to be broken down for any meaningful debugging, not to mention readability and maintainability are rather poor.



btw i think you'd be better off with using arrays to store multiple elements. I greatly dislike using unquoted variables for this purpose and depending on IFS to cut them down to individual parameters. My take is quote everything and use proper arrays when needed, also quoted. Can't go wrong with that.
When looking at someone else's code (or your own few months down the road) array syntax makes it immediately obvious that multiple elements are to be expected, while unquoted var could be a mistake and without going to the assignment you can never be sure. Arrays also make whitespace management a non-issue, unquoted vars not so much.

```

d=$(date +%m%d%Y -d yesterday )_sftpserver
old_image=( $( ec2-describe-images | awk -vd="$d" '$2~/ami-/ && $3~d { print $2; }' ) )
# or readarray -t old_image < <( ec2-describe-images | awk -vd="$d" '$2~/ami-/ && $3~d { print $2; }' )
printf "[%s]\n" "${old_image[@]}"

old_snaps=( $( ec2-describe-images "${old_image[@]}" | awk '$4~/snap/{print $4; }' ) )
# or readarray -t old_snaps < <( ec2-describe-images "${old_image[@]}" | awk '$4~/snap/{print $4; }' )
printf "[%s]\n" "${old_snaps[@]}"

for i in "${old_image[@]}"; do ...; done

for s in "${old_snaps[@]}"; do ...; done
```

---

### Post by ubuntpetbe2 on 2013-08-06
Until should work.?

---

### Post by Habitual on 2013-08-06
Thanks everyone, I am taking a break from this script for a few.

---

### Post by Habitual on 2013-08-11
Here is what I have got after a week or so "off" from this challenge:
```

#!/bin/bash
# dw_copy_dataworks.sh
# 08/11/2013 10:07:56 PM EDT
export TERM=linux
export EC2_HOME=/home/c9admin/ec2/ec2-api-tools/current
export PATH=$PATH:$EC2_HOME/bin
export JAVA_HOME=/usr
export AWS_ACCESS_KEY=
export AWS_SECRET_KEY=
export EC2_URL=https://ec2.us-west-2.amazonaws.com
ec2-copy-image -r us-east-1 --region us-west-2 -s $( awk 'NR==1 {print $2}' /home/c9admin/dwd/sftpserver.lst ) -n $(date '+%m%d%Y')_sftpserver -d "Daily sftpserver backup"
OLD_IMAGE=$( ec2-describe-images | awk -vd=$(date +%m%d%Y -d 'yesterday')_sftpserver '$2~"ami-" && $3~d { print $2; }' )
OLD_SNAPS=$(ec2-describe-images $(echo "$OLD_IMAGE") | awk '$4~/snap/ { print $4 }')

# Functions
sleep_timer()
{
sleep 1m
status_check
}

status_check ()
{
STATUS=$(ec2-describe-images --filter state=pending | grep $(date +"%m%d%Y")_sftpserver | awk 'NR==1 {print $5}')
if [[ $STATUS = "pending" ]] ; then
    sleep_timer
else
    for i in $OLD_IMAGE ; do ec2-deregister "$i" ; done
    for i in $OLD_SNAPS ; do ec2-delete-snapshot "$i" ; done
fi
}

status_check
exit 0
#EOF

```

I went this route because today, I noticed 
 ```
while RESULT=$(exec ec2-describe-images --filter state=pending | grep _smrtfocus); ; do sleep 1m ; done
        DE_REGISTER
        DEL_SNAPSHOTS
exit 0
```
did not exit the script and an hour after the Image became Available, it was still "running"...

Does it look like an infinite loop to anyone but me?
```

# Functions
sleep_timer()
{
sleep 1m
status_check
}

status_check ()
{
STATUS=$(ec2-describe-images --filter state=pending | grep $(date +"%m%d%Y")_sftpserver | awk 'NR==1 {print $5}')
if [[ $STATUS = "pending" ]] ; then
    sleep_timer
else
    for i in $OLD_IMAGE ; do ec2-deregister "$i" ; done
    for i in $OLD_SNAPS ; do ec2-delete-snapshot "$i" ; done
fi
[COLOR=#ff0000]**# seems like it "may" need an exit or return here?**[/COLOR]
}

status_check
exit 0
#EOF

```

I also did away with the DE_REGISTER and DEL_SNAPSHOTS functions and just used them "straight" in the else statement.
I can't see any reason why that won't be okay, but smarter people than I can read this and see a potential 'hiccup'

Thanks to all who contribute(d).

Edit:
I also did away with the while vs. until 'logic' as they both acted passive in the script.

---

### Post by Vaphell on 2013-08-11
can you post some example of the raw output that is supposed to keep the waiting going and one that should trigger the cleanup procedure? I will try to emulate the behavior using files and figure something out.

---

### Post by Habitual on 2013-08-12
Vaphell:

Sure, here is the full/sanitized output of a currently pending status using '[ec2-describe-images]("http://docs.aws.amazon.com/AWSEC2/latest/CommandLineReference/ApiReference-cmd-DescribeImages.html")':
```
ec2-describe-images --filter state=pending
IMAGE    ami-cnnnnnnn    012345678901/08122013_dataworks    012345678901    pending    private        x86_64    machine            windows    ebs    hvm    xen
BLOCKDEVICEMAPPING    EBS    /dev/sda1                false    standard    
BLOCKDEVICEMAPPING    EBS    xvdi                false    standard    
BLOCKDEVICEMAPPING    EBS    xvdh                false    standard    
BLOCKDEVICEMAPPING    EBS    xvdm                false    io1    4000
BLOCKDEVICEMAPPING    EPHEMERAL    /dev/xvdf    ephemeral0
BLOCKDEVICEMAPPING    EPHEMERAL    /dev/xvdg    ephemeral1
```


Also in the opening post ;)

As I said in post3, there are 3 scripts running in triplicate against three entities/hosts.
_dataworks
_smartfocus &
_sftpserver

I have to keep them separate for scheduling (10 0 * * 0,2-6 /path/to/script.sh) reasons.

You're a Star!

Thanks for keeping up with this.

---

### Post by Vaphell on 2013-08-12
```
#!/bin/bash

suffix=dataworks  #script parameter?
lst=/home/c9admin/dwd/${suffix}.lst  #lst depends on suffix?
td=$( date +%m%d%Y )_${suffix}
yd=$( date +%m%d%Y -d yesterday )_${suffix}
sleep=1


ec2-copy-image -r us-east-1 --region us-west-2 -s $( awk 'NR==1 {print $2}' "$lst" ) -n "$td" -d "Daily ${suffix^} backup"
OLD_IMAGE=( $( echo ec2-describe-images | awk -vd="$yd" '$2~/ami-/ && $3~d { print $2; }' ) ) #array
echo "OLD IMAGES (${#OLD_IMAGE[@]})"
printf "* %s\n" "${OLD_IMAGE[@]}"

OLD_SNAPS=( $( echo ec2-describe-images "${OLD_IMAGE[@]}" | awk '$4~/snap/ { print $4 }' ) ) #array
echo "OLD SNAPSHOTS (${#OLD_SNAPS[@]})"
printf "* %s\n" "${OLD_SNAPS[@]}"


#while ec2-describe-images | awk -vd="$td" ' && $3~d { print d, $5; exit $5=="available"; }'; do sleep $sleep; done #should work without filters?

while :   #infinite loop, jump out with break
do
  ec2-describe-images --filter state=available | grep -q "$td" && break
#  grep available in.txt | grep -q "$td" && break  # this line used to emulate effect of the line above
  echo "pending..."
  sleep $sleep
done
echo ":D"

for i in "${OLD_IMAGE[@]}" ; do echo "deregister $i"; done
for i in "${OLD_SNAPS[@]}" ; do echo "del-snapshot $i"; done
```

output i get is more or less like this
```
$ ./ec2.sh 
OLD IMAGES (0)
* 
OLD SNAPSHOTS (0)
* 
pending...
pending...
pending...
pending...
pending...   <changing 'pending' to 'available' in the dummy file>
:D
$
```

---

### Post by Habitual on 2013-08-12
Scary, but cool.
Some new concepts for me to have a look-see at.

I'll be checking in.... 
NOTE to Self: Don't use this on a Live System of my own? ;)

As usual, you rock!

I appreciate your time and efforts.
Thank you.

---

### Post by Vaphell on 2013-08-12
yup, for the time being don't use dereg and del-snapshot and see if everything is peachy during dry runs.

obviously remove *echo* in OLD_IMAGE/SNAP lines i used to make the script shut up about the missing command - i forgot to remove it-  configure sleep, lst file and what not to suit your needs.

No idea if the variables i defined are ok for your workflow but i assumed that the 3 variants are carbon copies of each other with that 1 word changing so i parametrized it. If that's the case you'd be able to roll a single script and call it with 3 different params.
As you can see i generated td (today) and yd (yesterday) to have the whole date+context combo readily available down the road.

conditions and conditional chaining of commands is all about exit codes.

if you have any questions about how and why something works (or at least should), ask.



Are you able to force the pending=>available situation at will?

---

### Post by Habitual on 2013-08-12
> **Vaphell said:**
> Are you able to force the pending=>available situation at will?

I'm not clear on what "pending=>available" means exactly.
The scripts  run daily in the middle of the night (EDT/New_York)

Most of the time, the dataworks server takes the longest amount of time, so it stays "pending" the longest.
Up to 16 hours on occasion.

I can always run an ec2-copy-image to the new region at will and explain it as "testing". I just have to manage the 
result manually, which Is what I'm doing now, daily removal of previous days' archives + snapshots.

I have free will as long as I can show "progress" ;)

I don't need the 
```
echo "OLD IMAGES (${#OLD_IMAGE[@]})"
...
echo "OLD SNAPSHOTS (${#OLD_SNAPS[@]})"

```
 
you say?
I use echo for "dry runs" and it's usually echo "$var[xyz]" 
I always strip it down the the bare bones and have been just REM'ing out the ec2-copy-image line and echo out the $vars.

parametrization is a great idea, as "the Boss" wants it to be template-able or cookie-cutter. You know...
change 2 lines of code and toss it in place for the next client.

It never ends.

Thanks!

---

### Post by Vaphell on 2013-08-12
pending=>available is the key moment triggering the cleanup, i wanted to know if you can manufacture it repeatably to speed up testing of the condition. I modified the dummy file like 50 times in a span of few minutes while testing various approaches. If the frequency at which tests can be performed are limited by real world then that sucks.
Do you have a terminal where you can spam commands freely? Can you run the script by hand?

these echos and associated printfs
echo "OLD IMAGES (${#OLD_IMAGE[@]})"
echo "OLD SNAPSHOTS (${#OLD_SNAPS[@]})"
are purely informative, ${#array[@]} returns the number of elements and printf line prints out the whole array, 1 elem at a time.

---

### Post by Habitual on 2013-08-12
> **Vaphell said:**
> If the frequency at which tests can be performed are limited by real world then that sucks.
Do you have a terminal where you can spam commands freely? Can you run the script by hand?
I'm a SysAdmin, I live in Terminal.

I cannot force that state at will, but I can just choose a smaller server image and run it by hand, yes. At will. at any time.
The _sftpserver being the smallest of the 3. It only has two volumes, one 1TB and One 8 G.

Edit: I removed "echo "[noparse]:D[/noparse]" cute as that appears.

---

### Post by Vaphell on 2013-08-12
> Edit: I removed "echo ":D" cute as that appears. 

lol :) i put it there to make it obvious in the pasted output that the loop ended. Obviously you are free to remove all non-essential printfs and echos

---

### Post by Habitual on 2013-08-12
We will see what we see in about 12 hours from now.

---

### Post by Habitual on 2013-08-12
Vaphell:

This looks 'funny' to me...
```
while :   #infinite loop, jump out with break
do
  ec2-describe-images --filter state=**[COLOR=#ff0000]available[/COLOR]** | grep -q "$td" && break
  echo "pending..."
  sleep $sleep
done
for i in "${OLD_IMAGE[@]}" ; do ec2-deregister "$i"; done
for i in "${OLD_SNAPS[@]}" ; do ec2-delete-snapshot "$i"; done
#EOF
```

Shouldn't that be state=pending ?

I need sleep.

---

### Post by Vaphell on 2013-08-12
if $td is found among the 'available' the loop is terminated instantly (break), if not the loop continues.
( AVAILABLE and TODAY ) => break

*break* depends on the successful exit code of *grep*, success is when the match is found.

i assume that the line with the proper timestamp/server is unique and you can't have 'pending' and 'available' at the same time

---

### Post by Habitual on 2013-08-13
Vaphell:

It appears to be "Production-Ready" as I ran it manually on a freshly copied ec2-copy-image on smrtfocus
```
pending...
57 more times...
IMAGE    ami-12345678
SNAPSHOT    snap-5c101c66
SNAPSHOT    snap-53101c69
SNAPSHOT    snap-55101c6f
```

The sleep variable allows us flexibility on what we know will be **big** jobs, so I can increase that for those.


```

#!/bin/bash
# 08/12/2013 08:31:48 PM EDT
# http://ubuntuforums.org/showthread.php?t=2164483&p=12754399#post127543990
export TERM=linux
export EC2_HOME=/home/c9admin/ec2/ec2-api-tools/current
export PATH=$PATH:$EC2_HOME/bin
export JAVA_HOME=/usr
export AWS_ACCESS_KEY=
export AWS_SECRET_KEY=
export EC2_URL=https://ec2.us-west-2.amazonaws.com

# Variables
suffix=sftpserver
lst=/home/c9admin/dwd/${suffix}.lst
sleep=1m

# Constants
td=$( date +%m%d%Y )_${suffix}
yd=$( date +%m%d%Y -d yesterday )_${suffix}

# Copy to us-west-2
ec2-copy-image -r us-east-1 --region us-west-2 -s $( awk 'NR==1 {print $2}' "$lst" ) -n "$td" -d "Daily ${suffix^} backup"

# Yesterday's IMAGE + SNAPSHOTS
OLD_IMAGE=( $( ec2-describe-images | awk -vd="$yd" '$2~/ami-/ && $3~d { print $2; }' ) ) 
OLD_SNAPS=( $( ec2-describe-images "${OLD_IMAGE[@]}" | awk '$4~/snap/ { print $4 }' ) )  

# Wait for "Available"
while :
do
  ec2-describe-images --filter state=available | grep -q "$td" && break
  sleep $sleep
done

# Delete Yesterday's IMAGE + SNAPSHOTS
for i in "${OLD_IMAGE[@]}" ; do ec2-deregister "$i"; done
for i in "${OLD_SNAPS[@]}" ; do ec2-delete-snapshot "$i"; done
#EOF

```

You have my respect and appreciation.

Thank you,
John Jones

---

### Post by Habitual on 2013-08-14
Vaphell:

Is this  a typo?
```
"Daily ${suffix**[COLOR="#FF0000"]^[/COLOR]**} backup"
```

today, it complained about bad substitution, so I removed it and ran it manually.

Thank you,

---

### Post by Vaphell on 2013-08-14
no, it's not a typo

```
$ suffix=sftpserver
$ echo "${suffix[COLOR="#0000FF"]^[/COLOR]} ${suffix[COLOR="#008000"]^^[/COLOR]}"
[COLOR="#0000FF"]S[/COLOR]ftpserver [COLOR="#008000"]SFTPSERVER[/COLOR]
```

version of bash?
If for whatever reason that doesn't work, just ignore it and use default value without modifications or whatever.

---

### Post by Habitual on 2013-08-14
GNU bash, version 3.2.25(1)-release (x86_64-redhat-linux-gnu) /CentOS release 5.9 (Final)

Thank you,

NOTE:
```
$ suffix=sftpserver
# echo "${suffix^} ${suffix^^}"
# -bash: ${suffix^} ${suffix^^}: bad substitution
```

case is not an issue. :)
and thanks for the color-coded 'tip'.

Edit0:
```
echo "${suffix}" | awk '{print toupper($0)}'
```

---

### Post by Vaphell on 2013-08-14
apparently these parameter expansions got added in later versions and servers tend to be conservative with updates. My desktop systems have v4.1.5 and later.

---

### Post by Habitual on 2013-08-14
"Daily ${suffix} backup" works for me, unless there's a reason not to use that?

---

### Post by Vaphell on 2013-08-14
it's pure aesthetics, so if you don't need it capitalized ${suffix} will be just fine.

BTW you don't have to keep my variable names, if 'context' or 'config' or 'server' better explain what happens than 'suffix', change it :-)

---

### Post by Habitual on 2013-08-14
No worries.
I'll leave you in peace now.

Thanks!

---

### Post by Vaphell on 2013-08-14
no problem, in fact after the forum hacking fiasco it's a bit slow here and now i am bored >_<

---

