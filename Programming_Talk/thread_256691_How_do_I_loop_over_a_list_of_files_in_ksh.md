---
title: "How do I loop over a list of files in ksh"
date: 2006-09-13
forum: Programming Talk
---

### Post by brundles on 2006-09-13
Getting a bit frustrated with this one now ](*,)  It's not really Ubuntu specific but given the wealth of knowledge on these forums I though I'd try my luck :mrgreen: 

I'm trying to write a ksh script to recurse down through a directory structure and run another program against any .avi files it finds. 

All is well until the script comes across a file or directory with a space in the title - because ksh uses space as the delimiter for a list :(. At this point it treats each word in the file name as an individual file.

Does anybody have any suggestions or recommendations on ways around this?

Thanks,
Keith

---

### Post by nereid on 2006-09-13
You can use the following command to get all .avi files

```

find DIRECTORY -type f -print0 -iname "*.avi"

```

Substitute DIRECTORY with your target directory or any other variable name. The list you'll get can be used in other commands.

---

### Post by brundles on 2006-09-13
Thanks for that suggestion Nereid - it's a simpler approach than I had been using.

Unfortunately it doesn't help with the problem that because ksh uses a space for it's list delimiter, I can't for a for each over the list when file names include spaces.

At the moment my (fairly inefficient!) script is basically the following ksh function:
```

function scanAndUnpack
{
  # First head down through all of the directories recursively
  echo "Scanning directories"
  SAU_DIR_LIST=`ls -d */`
  for SUB_DIR in ${SAU_DIR_LIST}
  do
    echo "Checking ${SUB_DIR}..."
    if [[ ! -w ${SUB_DIR} ]]
    then
      echo "No write access to ${SUB_DIR} - skipping."
    elif [[ ! -r ${SUB_DIR} ]]
    then
      echo "No read access to ${SUB_DIR} - skipping."
    else
      cd ${SUB_DIR}
      scanAndUnpack
      cd ..
    fi
  done
  echo "Finished scanning directories, starting on AVI files"
  
  # Then unpack the avi files found in this directory
  AVI_LIST=`ls *.avi`
  for AVI_FILE in ${AVI_LIST}
  do
    if [[ ! -r ${AVI_FILE} ]]
    then
      echo "No read access to ${AVI_FILE} - skipping."
    else
      PACK_STATE=`mono /opt/ninan/UnpackCL.exe -i ${AVI_FILE} | grep -i packed`
      if [[ ${PACK_STATE} = ${IS_PACKED} ]]
      then
        echo "${AVI_FILE} is packed - unpacking"
        mono /opt/ninan/UnpackCL.exe ${AVI_FILE} Unpacked_${AVI_FILE} > /dev/null
      
        # If the original is to be removed then do so
        if [[ ${REMOVE_ORIGINAL} = "TRUE" ]]
	then
	  echo "Removing ${AVI_FILE}"
	  rm ${AVI_FILE}	
	else
	  echo "Leaving original file"
	fi
 
      elif [[ ${PACK_STATE} = ${IS_UNPACKED} ]]
      then
        echo "${AVI_FILE} is not packed - skipping"
      else
        echo "Cannot determine pack state of ${AVI_FILE} - skipping"
      fi
    fi
  done
  echo "Finished scanning AVI files"
}

```

It works perfectly until it finds a directory or file name that has a space in it. e.g. "MyVideo.avi" works fine, but "My Video.avi" breaks as it thinks that's two files.

Can I get ksh to use either a different delimiter or realise that they're the same (for example if the filename is encapsulated in quotes?)

Thanks again,
Keith

---

### Post by nereid on 2006-09-14
The spaces should be handled by find. You get a list with each item in quotations.

Maybe you want to create a function for your processing and do something like this

```

find DIRECTORY -type f -print0 -iname "*.avi" | xargs -0r myBrandNewFunction

```

Which will feed your function with the whole list (with spaces and so on).

---

### Post by brundles on 2006-09-14
Well that's made things much simpler :D 

Thanks very much =D> =D> =D> =D>

---

### Post by nereid on 2006-09-14
No problem, glad that it is working.

---

