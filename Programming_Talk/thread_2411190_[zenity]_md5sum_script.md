---
title: "[zenity] md5sum script"
date: 2019-01-26
forum: Programming Talk
---

### Post by zergling on 2019-01-26
Hello everyone,

I am trying to create a script that after selecting a directory via zenity, the script will recursively go through every files and create a single md5 file.
Everything works great but I would like to delete the md5 file in case the user cancel or closes the dialog window during the creation of the md5 file.

How would I do that?

This is the code.

```

#!/bin/bash

location=$(zenity --file-selection --directory)
if [[ -z $location && ${location+x} ]]; then
  exit 0
else
  cd $location

  # ex: location=/home/zergling/test
  # ${location##*/} will remove the last / and everything before that
  # so, ${location##*/}.md5 is going to be test.md5
  (
    echo "# creating md5sum..."
    find -type f \( -not -name "${location##*/}.md5" \) -exec md5sum '{}' \; > ${location##*/}.md5
  ) | zenity --title="Running..." --progress --pulsate --auto-close  &

  #### I got the below code from the Internet ######  

  # get zenity process id
  PID_ZENITY=${!}

  # get firstly created child process id, which is running all tasks
  PID_CHILD=$(pgrep -o -P $$)

  # loop to check that progress dialog has not been cancelled
  while [ "$PID_ZENITY" != "" ]
  do
    # get PID of all running tasks
    PID_TASKS=$(pgrep -d ' ' -P ${PID_CHILD})

    # check if zenity PID is still there (dialog box still open)
    PID_ZENITY=$(ps h -o pid --pid ${PID_ZENITY} | xargs)

    # sleep for 2 second
    sleep 2
  done

  # if some running tasks are still there, kill them
  [ "${PID_TASKS}" != "" ] && kill -9 ${PID_TASKS}
fi

```

I am open to any suggestion and improvements.

---

### Post by howefield on 2019-01-26
Thread moved to the "*Programming Talk*" forum.

---

### Post by SeijiSensei on 2019-01-26
I don't know anything about zenity, but it sounds like you want to create a single MD5 summary that corresponds to all the files in a directory.  I'd just create a tar archive of all the files and take the MD5 summary of that.

```

cd /directory
tar -cvf - . | md5sum

```

That creates a tar archive of all the files in the current directory, represented by the dot, then writes that archive to standard output ("-") where it is piped ("|") as input to the md5sum command.  The "v" switch lets you follow tar's progress through your files. 

If you want to create and store the archive as a file then create its MD5 summary, I suggest using the bzip compressor (the "-j" switch) like this:
```

cd /directory
tar -cjvpf ../archive.tar.bz2 . 
md5sum < ../archive.tar.bz2

```

The "-p" switch preserves things like permissions and creation times.

---

### Post by SagaciousKJB on 2019-01-29
> **zergling said:**
> Hello everyone,

I am trying to create a script that after selecting a directory via zenity, the script will recursively go through every files and create a single md5 file.
Everything works great but I would like to delete the md5 file in case the user cancel or closes the dialog window during the creation of the md5 file.

How would I do that?

This is the code.

```

#!/bin/bash

location=$(zenity --file-selection --directory)
if [[ -z $location && ${location+x} ]]; then
  exit 0
else
  cd $location

  # ex: location=/home/zergling/test
  # ${location##*/} will remove the last / and everything before that
  # so, ${location##*/}.md5 is going to be test.md5
  (
    echo "# creating md5sum..."
    find -type f \( -not -name "${location##*/}.md5" \) -exec md5sum '{}' \; > ${location##*/}.md5
  ) | zenity --title="Running..." --progress --pulsate --auto-close  &

  #### I got the below code from the Internet ######  

  # get zenity process id
  PID_ZENITY=${!}

  # get firstly created child process id, which is running all tasks
  PID_CHILD=$(pgrep -o -P $$)

  # loop to check that progress dialog has not been cancelled
  while [ "$PID_ZENITY" != "" ]
  do
    # get PID of all running tasks
    PID_TASKS=$(pgrep -d ' ' -P ${PID_CHILD})

    # check if zenity PID is still there (dialog box still open)
    PID_ZENITY=$(ps h -o pid --pid ${PID_ZENITY} | xargs)

    # sleep for 2 second
    sleep 2
  done

  # if some running tasks are still there, kill them
  [ "${PID_TASKS}" != "" ] && kill -9 ${PID_TASKS}
fi

```

I am open to any suggestion and improvements.

At this point...

```
(
    echo "# creating md5sum..."
    find -type f \( -not -name "${location##*/}.md5" \) -exec md5sum '{}' \; > ${location##*/}.md5
  ) | zenity --title="Running..." --progress --pulsate --auto-close  &
```

The return status of zenity should be checked.  bash stores this in the variable '$?'.

Something like

```
if [ $? !=0 ] ; then rm ${location##*/}.md5 ; fi
```

Note that since '$?' hold's the most previous command's return status, the test must be ran IMMEDIATELY after the zenity command.  Since you're forking it to the background, that may create race conditions.

According to zenity's man page, the program will return 1 if "Cancel" is pressed and 0 if "OK'.

---

