---
title: "Download Accelerator for streaming."
date: 2012-09-04
forum: Programming Talk
---

### Post by xvan on 2012-09-04
Hey.
I wasn't able to find a download accelerator that allowed me to specify small chunks and downloaded them in order to allow a "pseudo streaming"...

I made this script with curl that works, but its really really ugly.
How do I make it less ugly? like resuming downloads.

I needed two things that I had never done in any language:
It's my first pseudo threaded application.
Simultaneously writes to the same file from several "threads" (curl forks).

Probably I solved it the wrong way (or with the wrong language), as I see it really hard to implement a download resume or  show the download speed reported by curl.

```

#!/bin/bash
#DOWNLOAD ACCELERATOR TEST
#FIRST ARGUMENT IS THE FILE TO DOWNLOAD

curl --head $1
SIMUL=4 #number of simultaneous connections
SIZE=$( curl --head $1  | grep Content-Length | grep -o "[0-9]*")
#NK IS MAX CHUNK SIZE IN BYTES
#NK="5242880" #5MB CHUNK
NK=1048576 #1MB CHUNK
#NK=1 #1B CHUNK
TIMES=$(( SIZE / NK ))
echo TIMES $TIMES
echo SIZE $SIZE
echo NK $NK
l=0
while read k
    do
    while [ $( ps aux |grep '[c]url .*'"$1" | wc -l) -ge $SIMUL ];  do sleep 1; done
    echo CHUNK $k
    echo SIZE $(( -1 *  ( $k - 1 ) ))
    curl -r $k -s $1  |  dd bs=$NK  of=out.test seek=$l oflag=nonblock conv=notrunc &> /dev/null &
#NEEDED TO USE NOTRUNC TO ALLOW OUT OF ORDER CHUNK WRITE. 
#bs=$NK EXCEPT FOR  THE LAST CHUNK, BECAUSE NOTRUNC COMPLETES IT WITH TRASH.
                                  
    let l++
    done < <( for i in $( seq 1 $TIMES )
                      do
                          echo $(( ( i - 1 ) * NK    ))-$(( i * NK - 1 )) 
                      done
                      if [ $(( SIZE % NK )) -ne 0 ]
                      then 
                          echo $(( NK * TIMES  ))-$(( SIZE - 1 ))
                      fi
                      ) #THIS GENERATES THE LIST OF CHUNKS

while ps aux |grep '[c]url .*'"$1" -q  ;  do sleep 1; done #wait for end
echo END;

```Any Ideas are apreciated.

---

