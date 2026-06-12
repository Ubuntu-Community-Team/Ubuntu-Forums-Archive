---
title: "Hotfolder with inotify-tools, loop FOR not working"
date: 2018-04-05
forum: Programming Talk
---

### Post by alessandro19 on 2018-04-05
I can not understand why this little script with a loop processes only one file.

At boot in /etc/rc.local i wrote:

    ```
/usr/local/bin/./myscript &

```
This is myscript:

  ```
#!/bin/bash
    while inotifywait -e create /HOTFOLDER/ ; do

    for fullname in /HOTFOLDER/*.xlsx; do
 
    if ! [ -d "$fullname" ]; then
            send=/HOTFOLDER/$(date +'SEND-%F')
            sleep 10s
                    mkdir -p $send
                    mv -- "$fullname" $send
    fi

    done
    done
```

I have try also the option -m in inotifywait, but same problem:

   ```
while inotifywait -m -e create /HOTFOLDER/ ; do
```

---

### Post by Rocket2DMn on 2018-04-05
What is it that you're actually trying to do?  If you're trying to move xslx files to the directory you create, try something more like:
```

#!/bin/bash
DIR="./testdir"
while true; do
    inotifywait -e create "$DIR"
    # Check the exit code was good
    if [ $? -eq 0 ]; then
        # Get all .xslx files in $DIR
        for fullname in $(find "$DIR" -maxdepth 1 -name "*.xslx" -type f); do
            send="$DIR"/$(date +'SEND-%F')
            sleep 10s
            mkdir -p "$send"
            # Move the file to the directory we created
            mv "$fullname" "$send"
        done
    else
        echo "inotifywait failed"
        exit 1
    fi
done

```

It doesn't seem like you wanted to iterate over the output of inotifywait (although you could if you want, to parse the name of the file it saw created, but you might miss some files when inotifywait isn't running).

---

### Post by alessandro19 on 2018-04-06
> **Rocket2DMn said:**
> What is it that you're actually trying to do?  If you're trying to move xslx files to the directory you create, try something more like:
```

#!/bin/bash
DIR="./testdir"
while true; do
    inotifywait -e create "$DIR"
    # Check the exit code was good
    if [ $? -eq 0 ]; then
        # Get all .xslx files in $DIR
        for fullname in $(find "$DIR" -maxdepth 1 -name "*.xslx" -type f); do
            send="$DIR"/$(date +'SEND-%F')
            sleep 10s
            mkdir -p "$send"
            # Move the file to the directory we created
            mv "$fullname" "$send"
        done
    else
        echo "inotifywait failed"
        exit 1
    fi
done

```

It doesn't seem like you wanted to iterate over the output of inotifywait (although you could if you want, to parse the name of the file it saw created, but you might miss some files when inotifywait isn't running).

Thank you
I have try your script but it's not work... (error in mv command, unable to finde file or directory .... very strange)

but the problem with myscript:  

If in the HOTFOLDER there are 10 .xlsx files and then I copy a new one, the **loop works all file** to the end.
  If there is no file inside the HOTFOLDER and then I copy 10.xlsx, the [B]loop processes only one


[/B]

---

### Post by Rocket2DMn on 2018-04-06
My example script set uses a different directory tha /HOTFOLDER/ since I don't have that on my system.  See the $DIR variable and make sure you set that properly.

I'm also not sure your if statement "for fullname in /HOTFOLDER/*.xlsx; do" will work correctly, I have trouble using wildcards after paths (e.g., "in *.xslx" works but not "in /HOTFOLDER/*.xslx").

I think there is a race-like condition happening.  The for loop is evaluated before the remaining 9 xslx files are actually copied to the directory.  So it only recognizes the first file.  You may want to make the for loop a while loop and checks for xslx files after processing each one.  This may not solve your problem entirely though since a file could potentially appear after the for (or while) loop exits but before inotifywait is invoked again.

---

### Post by alessandro19 on 2018-04-12
thank you

---

