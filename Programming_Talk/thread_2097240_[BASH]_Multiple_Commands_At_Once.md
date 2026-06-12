---
title: "[BASH] Multiple Commands At Once"
date: 2012-12-22
forum: Programming Talk
---

### Post by thegodfaza on 2012-12-22
I'm building a myhttv transcode script and it's now working correctly, but I want to see the progress through the WebUI. To update the progress, a table has to be modified in the mysql database. So I need to run HandbrakeCLI, take the output in real time, which looks similar to this "Encoding: task 1 of 1, 20.20 % (46.70 fps, avg 42.42 fps, ETA 00h48m25s)", and update a database every couple of seconds with this information. The current script looks like this:
```
#!/bin/sh

# Transcodes to x264 @ 720p (1280x720) using handbrake-cli

# Arguments
# $1 must be the directory/file to be transcoded.
# $2 must be the output directory / file name. The directory must be writeable by the mythtv user
# $3 must be chanid
# $4 must be starttime
# the full userjob command in mythtv-setup should look like this: /path/to/this-script/mythtv-transcode-convert2x264 "%DIR%/%FILE%" "%DIR%/%TITLE% - %PROGSTART%.mkv" "%CHANID%" "%STARTTIMEUTC%"

# MySQL database login information (for mythconverg database)
DATABASEUSER="mythconverg"
DATABASEPASSWORD="*********"
DATABASENAME="mythconverg"

updatestatus() # $1-chanid, $2-starttime, $3-message
{
	local chanid=$1 starttime=$2 message=$3

	cat << EOF | mysql -u ${DATABASEUSER} -p${DATABASEPASS} ${DATABASENAME}
UPDATE
	jobqueue
SET
	comment='${message}'
WHERE
	chanid='${chanid}'
AND
	starttime='${starttime}'
AND
	type='256'
AND
	status='4';
EOF
}

# don't change these
DIRNAME=`dirname "$2"`
BASENAME=`echo "$2" | awk -F/ '{print $NF}' | sed 's/ /_/g' | sed 's/://g' | sed 's/?//g'`
ARCHIVEDIR="${DIRNAME}/originals"

# convert with handbrake
nice HandBrakeCLI -e x264 -q 16 -E copy --audio-copy-mask ac3,dts,dtshd --audio-fallback ffac3 -w 1280 --crop 0:0:0:0 -i "$1" -o "${DIRNAME}/${BASENAME}"
 
# update the database to point to the transcoded file and archive the original recorded show.
NEWFILESIZE=`du -b "$DIRNAME/$BASENAME" | cut -f1`
cat << EOF | mysql -u ${DATABASEUSER} -p${DATABASEPASS} ${DATABASENAME}
UPDATE
	recorded
SET
	basename='${BASENAME}',
	filesize='${NEWFILESIZE}',
	transcoded='1'
WHERE
	chanid='${3}'
AND
	starttime='${4}';
EOF
mv $1 $ARCHIVEDIR/${1}.x264.old
rm $1.png
```

---

### Post by trent.josephsen on 2012-12-22
I'm not seeing a question in your post.

---

### Post by thegodfaza on 2012-12-22
> **trent.josephsen said:**
> I'm not seeing a question in your post.

> **thegodfaza said:**
> So I need to run HandbrakeCLI, take the output in real time, which looks similar to this "Encoding: task 1 of 1, 20.20 % (46.70 fps, avg 42.42 fps, ETA 00h48m25s)", and update a database every couple of seconds with this information.

The question is stated implicitly. How would one accomplish this task?

---

### Post by ofnuts on 2012-12-22
> **thegodfaza said:**
> The question is stated implicitly. How would one accomplish this task?Create named pipe, start the process in background with output to the pipe, and read the pipe / update DB in your main script?

---

### Post by thegodfaza on 2012-12-22
> **ofnuts said:**
> Create named pipe, start the process in background with output to the pipe, and read the pipe / update DB in your main script?

I need to do this in a single script. Would this still be possible? Also after the conversion is finished the script needs to continue to update database entries. How would I detect when the transcode is finished if it's no longer part of the script? Similarly, the main script would need to know when the transcode is finished to stop updating the database and tell mythtv the job was successful with a code 0.

Basically what I'm looking for is a way to pipe the output from the transcode into a function that will update the database every so often and when the transcode is finished it stops and continues with the execution of the script.

---

### Post by ofnuts on 2012-12-22
> **thegodfaza said:**
> I need to do this in a single script. Would this still be possible? Also after the conversion is finished the script needs to continue to update database entries. How would I detect when the transcode is finished if it's no longer part of the script? Similarly, the main script would need to know when the transcode is finished to stop updating the database and tell mythtv the job was successful with a code 0.

Basically what I'm looking for is a way to pipe the output from the transcode into a function that will update the database every so often and when the transcode is finished it stops and continues with the execution of the script.
When you start a baground process its PID is returned in $! so you can check if it's still running.

The command you start in background can be another instance of your script (use a specific parameter to distinguish cases)

```

function run_in_background
{
    # whatever
}

function run_in_foreground 
{
      #Launch background
      $0 "*BACKGROUND*"
       backgroundpid=$!
}

if [[ "$1" == "*BACKGROUND*" ]]
then
   run_in_background()
else
  run_in_foreground()
fi

```

and to check the process is still running:
[code]
        kill -0 $backrgoundpid
[/code

---

### Post by thegodfaza on 2012-12-23
OK, now it's mostly working. I start the transcode as a background process and send it's output into a named pipe. And outside the script I can read the contents of the named pipe by using "cat /path/to/fifopipe" but it seems the pipe is a stream and when I try to do anything with it's contents my script locks up until the stream stops. I also see this when running cat or trying to store it to a variable in bash. Bash locks until I hit ctrl+c. I'm guessing that "PIPECONTENTS=`cat $FIFOPIPE`" is not the right way to capture the current contents of a named pipe to a variable?
```

FIFOPIPE="/tmp/${3}.${4}.pipe"

[...]

# convert with handbrake
mkfifo ${FIFOPIPE} # creates a named pipe
echo "Starting transcode."

nice HandBrakeCLI -e x264 -q 16 -E copy --audio-copy-mask ac3,dts,dtshd --audio-fallback ffac3 -w 1280 --crop 0:0:0:0 -i "$1" -o  "${DIRNAME}/${BASENAME}" >${FIFOPIPE} & # start the transcode and push the process into the background
PID=$! # capture the PID of the transcoding process

# makes nice status updates for mythweb
echo "Starting while loop."
while true
do
	RUNNING=`kill -0 $! &> /dev/null;echo $?` # is the transcoder running?
	PIPECONTENTS=`cat $FIFOPIPE`
	if [[ ${RUNNING} ]]; then # exit while loop when transcoder finishes
		rm -rf ${FIFOPIPE}
		$(updatestatus "${3}" "${4}" "Transcode Complete")
		break
	else
		$(updatestatus "${3}" "${4}" "${PIPECONTENTS}") # output status of the transcode job
		sleep 5 # only output status every 5 seconds
	fi
done
```

Another problem I'm having is that my mysql command will not execute when I use variables to define the username and password. I have to put them inline for it to work. Ex:
```
# This works
cat << EOF | mysql -u username -ppassword database
SQL
EOF

# This does not work
USERNAME="username"
PASSWORD="password"
DATABASE="database"
cat << EOF | mysql -u $USERNAME -p$PASSWORD $DATABASE
SQL
EOF
```

---

### Post by thegodfaza on 2012-12-23
I've also tried using read but it doesn't seem to work either. Script locks up once it gets to the read line.
```
while true
do
	if read -u 3 text
	then
		RUNNING=$(kill -0 $PID &> /dev/null;echo $?) # is the transcoder running?
		PIPECONTENTS=$text
		echo "Pipe contains: $PIPECONTENTS"
		if [[ ${RUNNING} == 1 ]]; then # exit while loop when transcoder finishes
			rm -rf ${FIFOPIPE}
			$(updatestatus "${3}" "${4}" "Transcode Complete")
			break
		else
			$(updatestatus "${3}" "${4}" "${PIPECONTENTS}") # output status of the transcode job
			sleep 5 # only output status every 5 seconds
		fi
	fi
done 3< "$FIFOPIPE" 4> "$FIFOPIPE"
```

Edit:
Working with the pipe from the bash shell, I have the same problem.
```

$ cat /tmp/1551.20121222190000.pipe
Encoding: task 1 of 1, 7.26 % (52.80 fps, avg 32.45 fps, ETA 00h50m33s)^C
$ while read data
> do
> echo $data
> break
> done </tmp/1551.20121222190000.pipe
^C
```
However when I pipe /dev/random into a pipe the code works just fine.
```
$ mkfifo /tmp/testpipe
$ cat /dev/random > /tmp/testpipe &                            [2] 29198
$ while read testpipe
> do
> echo $testpipe
> break
> done </tmp/testpipe
lQ&#9618;&#9618;&#9618;&#9618;&#9618;Vs&#9618;&#9618;k&#9618;4?&#9618;&#9618;&#9618;J&#488;nj&#9618;&#9618;P&#9618;&#9618;L&#9618;Q&#9618;8
```
Perhapse the problem lies with the way that handbrake-cli returns output?

---

### Post by thegodfaza on 2012-12-27
Well it's been four days and I've been messing around with some more related scripts. It seems the problem is, as I had guessed, that handbrake is outputting it's status updates in a way that I can't read. I was messing around with mythcommflag and it seems it also outputs in a similar way.
```
$ mythcommflag --chanid 1071 --starttime 20121226223500 &> /tmp/out 2>&1
$ tail -f /tmp/out
2012-12-27 21:02:38.957334 E  AFD: Unknown audio decoding error
2012-12-27 21:02:39.365666 E  AFD: Unknown audio decoding error
 48000/ 518fps
$ tail /tmp/out
2012-12-27 21:02:38.957334 E  AFD: Unknown audio decoding error
2012-12-27 21:02:39.365666 E  AFD: Unknown audio decoding error
$ while true; do if read test; then echo $test; sleep 5; fi; done </tmp/out
2012-12-27 21:02:38.957334 E  AFD: Unknown audio decoding error
2012-12-27 21:02:39.365666 E  AFD: Unknown audio decoding error
```
As you can see, when I set the follow flag using tail I can see the progress of the job but when I don't or I try and extract the output and store it to a variable I get everything but the real time progress. Is there a way to capture the real time progress part of the output "48000/ 518fps"?

---

