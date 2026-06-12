---
title: "file transfer notifier bash script I wrote"
date: 2006-11-28
forum: Programming Talk
---

### Post by russellchamp on 2006-11-28
Bash scripting is fun!  I even took a class at the local community college on "Linux Scripts and Tools" but I never really had a chance to USE the knowledge.
Here's a nifty script to monitor large file transfers.  I wrote it because I was transferring a lot of data from my external hard drive to my server and wanted to monitor where it was at.  I only have USB 1 on the server and I was transferring around 150GB of data so I found it quite useful!

I'd like some feedback on my work.  I'm still a newb at bash scripting so I'm sure there are multiple "better" or more efficient ways to do this...

------------------------------
#showtransfer v5

#written by Russell Champoux on 11/27/2006
#the purpose is to see the current transfer status between two directories
  #option -f: displays the "full" second directory layer of items being transfered
#first argument is the directory copied FROM
#the second argument is the directory being copied TO
#NOTE: the script "breaks" if there are more files in the "coppied to" directory than the "coppied from directory"

clear
full=0

while getopts ":f:" Option
do
  case $Option in
    f   ) full=1;;
    *   ) full=0;;
  esac
done

if [ $full -eq 1 ]
then
  shift 1
fi

fromdir=$1
todir=$2
echo Files transfered from : $fromdir
echo Files transfered to   : $todir

cd $fromdir
for dir in *
do
  done=`ls -l "$todir"/"$dir" 2> /dev/null | wc -l`
  if [ -d "$todir"/"$dir" ]
  then
    done=$(($done - 1))
  fi

  outof=`ls -l "$fromdir"/"$dir" 2> /dev/null | wc -l`
  if [ -d "$fromdir"/"$dir" ]
  then
    outof=$(($outof - 1))
  fi


  echo $done of $outof files transfered to $dir
  if [ $full -eq 1 ]
  then
    if [ -d "$fromdir"/"$dir" ]
    then
      cd "$fromdir"/"$dir"

      for subdir in *
      do
        subdone=`ls -l "$todir"/"$dir"/"$subdir" 2> /dev/null | wc -l`
        suboutof=`ls -l "$fromdir"/"$dir"/"$subdir" 2> /dev/null | wc -l`
        echo \*\*\* $subdone of $suboutof files transfered to $subdir
      done
    fi
    echo
  fi
done
echo
-----------------------------

Once again, if you look at this, tell me what you think.  Cool?  Crap?  Useful?  Pointless?  Tell me what it is you're thinking.

---

