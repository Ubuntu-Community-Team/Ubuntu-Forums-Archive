---
title: "More bash scripting... crazy brackets?"
date: 2005-11-22
forum: Programming Talk
---

### Post by endy on 2005-11-22
Hi, I thought it was about time I too learned some bash scripting and as I use Easynews' excellent services I thought I'd make something related to that.

As far as I can tell this works as it's supposed to, that is  you can pass any valid  download queue number (1 to 10) as an argument and the script will download those zip queues or pass it "a" to download all of them, pass no argument and it prints some help text.

What I was wondering was have I done the conditions for the if statements the best way? I can't help but think I've gotten lost regarding parenthesis. 

Any comments or suggestions?


```
#!/bin/bash
# Download from easynews.com, with arguments
#
# Original command for reference:
# wget -H -c -nd -r -l1 --no-check-certificate --http-user="USERNAME" --http-passwd="PASSWORD" \
#    -I"/news/" -Rremove "https://secure.members.easynews.com/zipmanager.html?editzip=Q01&.remove"
#
#

PARMS_1="-H -c -nd -r -l1 --no-check-certificate"
PARMS_2="-I"/news/" -Rremove"
USER="username"
PASS="password"
URL1="https://secure.members.easynews.com/zipmanager.html?editzip=Q"
URL2="&.remove"
QUEUE="01 02 03 04 05 06 07 08 09 10"
ALL_CMD="a"

if [ ! -n "$1" ]
then
  echo "Usage: `basename $0` queue1, queue2, etc..."
  echo "Queue numbers can be 1 to 10 or use \"$ALL_CMD\" to get all queues."
  echo "Exit."
  exit
fi 

# Test that the arguements are valid (within 1 to 10 or $ALL_CMD)
for arg in $*
do
if (( ($arg > 10) || ($arg < 1) )) && [[ $arg != $ALL_CMD ]]
    then
    echo "Bad argument:" \"$arg\"
    echo "Only queue numbers between 1 to 10 and \"$ALL_CMD\" are allowed."
    echo "Exit."
    exit
  fi 
done

# Test for $ALL_CMD parameter and if so download ALL queues and exit, ignoring all other arguments
for arg in $*
do
  if [[ $arg == $ALL_CMD ]]
    then
      for queue in `echo $QUEUE`
      do
     wget $PARMS_1 --http-user=$USER --http-passwd=$PASS $PARMS_2 $URL1$queue$URL2
      done
   exit
  fi
done

# Otherwise download the selected queues
for arg in $*
do
  if [[ $arg == 10 ]]
    then wget $PARMS_1 --http-user=$USER --http-passwd=$PASS $PARMS_2 $URL1$arg$URL2
  else 
    wget $PARMS_1 --http-user=$USER --http-passwd=$PASS $PARMS_2 $URL1"0"$arg$URL2
  fi
done

exit 0
```

---

### Post by zenzenzenzen on 2008-04-17
I'll be honest with you, I'm a perl guy.  I don't know if your brackets are right or not. 

I did however hack up your script a little bit.  I'm also not sure if this is the best way to do it, or not.  I wanted to be able to right-click->copy link, and paste it to the cli from the global4 search results page.  I had been doing this with a bashrc alias that just called wget -c with my name and password before, and it seemed to compliment your script well, so I added the functionality to it.

basically, when you call the script now, you can either use a number or 'a' like in the original, or you can paste one or more easynews urls (starting with http), and it will download those.  This is useful if you want to use wget as your download ap (I've found I get better results speed-wise with it than with, say, firefox), but only need one file, and don't want to take the extra step of adding it to your zip manager.

It was also an excuse to learn some more bash (like you).  Today I learned how to make echo use bold text, so I added some more output for the user.

Anyone know if there is a better way to use a regex in a bash "if" statement?  I couldn't figure out how to get it to work, so I cheated and piped echo to egrep.

in perl it would be something like:
 ```

if ( $1 =~ /^$HTTP/i ) { do this }

```

but I'm not really sure how that translates to bash.  so anyways, like you, I know it at least works like it is, and that's good enough for me. :)

Anyways, I thought I'd put a copy of my changes up here in case anyone else could use them or improve on it some more.

Nice idea for a script, by the way.  thanks :)

```

#!/bin/bash
# Download from easynews.com, with arguments
#
# Original command for reference:
# wget -H -c -nd -r -l1 --no-check-certificate --http-user="USERNAME" --http-passwd="PASSWORD" \
#    -I"/news/" -Rremove "https://secure.members.easynews.com/zipmanager.html?editzip=Q01&.remove"
#
#

PARMS_1="-H -c -nd -r -l1 --no-check-certificate"
PARMS_2="-I"/news/" -Rremove"
USER=""
PASS=""
URL1="https://secure.members.easynews.com/zipmanager.html?editzip=Q"
URL2="&.remove"
QUEUE="01 02 03 04 05 06 07 08 09 10"
ALL_CMD="a"
HTTP="http://"

if [ ! -n "$1" ]
then
  echo -e "\033[1m`basename $0`:\033[0m Downloads files from easynews."
  echo
  echo -e "\033[1mZip-manager:\033[0m"
  echo -e "Usage: `basename $0` queue1, queue2, etc..."
  echo "Queue numbers can be 1 to 10 or use \"$ALL_CMD\" to get all queues."
  echo
  echo -e "\033[1mSearch results:\033[0m"
  echo -e "Usage: `basename $0` url1 url2 url3 etc..."
  echo -e "URLs can be copy and pasted directly from search results page, and \033[1mmust\033[0m start with $HTTP."
  echo  
exit
fi 

# Just get the list of urls, if that is all we want
if [[ `echo $1 | egrep ^$HTTP` ]]
    then
	for urls in $*
	do	
	if [[ $urls != $SEARCH ]]
	then
     	  echo "Fetching url $urls"
	  wget -c --http-user=$USER --http-passwd=$PASS $urls
	  echo "Done"
	fi
	done
   exit
fi

# Test that the arguements are valid (within 1 to 10 or $ALL_CMD)
for arg in $*
do
if (( ($arg > 10) || ($arg < 1) )) && [[ ( $arg != $ALL_CMD ) ]]
    then
    echo -e "\033[1mBad argument:\033[0m" \"$arg\"
    echo "Only queue numbers between 1 to 10 and \"$ALL_CMD\" are allowed."
    echo "Exit."
    exit
  fi 
done

# Test for $ALL_CMD parameter and if so download ALL queues and exit, ignoring all other arguments
for arg in $*
do
  if [[ $arg == $ALL_CMD ]]
    then
      for queue in `echo $QUEUE`
      do
     	echo -e "\033[1mFetching all queues.  Progress:\033[0m queue $queue"
  	wget $PARMS_1 --http-user=$USER --http-passwd=$PASS $PARMS_2 $URL1$queue$URL2
	echo -e "\033[1mDone\033[0m"
      done
   exit
  fi
done

# Otherwise download the selected queues
for arg in $*
do
  if [[ $arg == 10 ]]
  then
    echo -e "\033[1mFetching queue\033[0m 10"
    wget $PARMS_1 --http-user=$USER --http-passwd=$PASS $PARMS_2 $URL1$arg$URL2
  else 
    echo -e "\033[1mFetching queue\033[0m $arg"
    wget $PARMS_1 --http-user=$USER --http-passwd=$PASS $PARMS_2 $URL1"0"$arg$URL2
  fi
done
echo -e "\033[1mDone\033[0m"
exit 0

```

---

### Post by zenzenzenzen on 2008-04-17
ok, so I just noticed this thread is like 2+ years old.  oh well, maybe it will be useful to someone :P

---

### Post by seffyroff on 2008-11-16
Very useful indeed, thanks to both!

---

