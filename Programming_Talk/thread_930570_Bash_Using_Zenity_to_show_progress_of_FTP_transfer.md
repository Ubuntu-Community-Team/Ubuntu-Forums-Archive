---
title: "Bash: Using Zenity to show progress of FTP transfer"
date: 2008-09-26
forum: Programming Talk
---

### Post by davidryder on 2008-09-26
I am creating an automated screenshot script that uploads the image to FTP and I want to output the progress of the transfer to zenity. Here is what I have:

```

function send() {
lftp ftp.phpstory.net<<-EOF
user $ftp_user $ftp_pass
cd $ftp_save_dir
put "$ufile"
bye
EOF
} 

send | zenity --progress --title="Screenshot" --auto-kill --auto-close --text="Uploading ($filesize)..." --percentage="0"

```

I have tried a variety of things including different ftp programs but the result is all the same: the progress bar doesn't move until the transfer is complete. At that time the progress bar instantly fills to 100%. I chose lftp because it actually displays a percentage complete on the command line but for I haven't been able to pipe that into zenity.

I would appreciate any help!

---

### Post by SeanHodges on 2008-09-26
The zenity progress bar takes an incrementing number as it's input. This number must increment as a whole number from 0 to 100. Try the example below:

```
for ((i=0;i<=100;i+=10))
do
    echo "$i"
    sleep 1
done | zenity --progress --title="Screenshot" --text="Uploading..." --percentage="0"
```

Your send() function does not provide this number, I would suggest you loop through the files you are FTP'ing (using a loop similar to above), lftp each one individually, and echo the percentage of files that have been transferred.

---

### Post by davidryder on 2008-09-26
Thanks for the reply...

The problem is the send() function is only executed once (one file) each time the script runs.

---

