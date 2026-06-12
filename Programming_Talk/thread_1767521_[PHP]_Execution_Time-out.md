---
title: "[PHP] Execution Time-out"
date: 2011-05-25
forum: Programming Talk
---

### Post by Daniel5 on 2011-05-25
Salutations!

I'm needing to read a file from another web host and write it to a local file on my own web host via PHP. The files I'm going to be downloading are well in the hundred megabytes. With my hosts lightning fast (compared to mine) down speed which I can download almost the entire file with before getting the execution time-out error.

We can't change the time-out length via set_time_limit  and cURL isn't installed. Also we can't use require(), include(), fopen() or file_get_contents() due to safe mode being enabled (passing any of those functions a link starting with http:// or www won't get us far). Lastly php.ini and .htaccess are a no go. So I'm forced to use fsockopen() to open a handle and read it with fread() But like I said a tad before we've downloaded the entire file we get the time-out error.

Can anyone cook up an idea of bypassing this time-out and still use fsockopen()?

[http://pastebin.com/dCMUrfwj](http://pastebin.com/dCMUrfwj)

---

### Post by Reiger on 2011-05-25
It might be possible to fork your script (allowing you to use multiple sockets in parallel) and download sections of the big file in parallel using HTTP range requests (allowing you to cut the download time to within limits). Then you'd need some server side logic to deal with the fact that your original single file is now a bunch of parts.

But why do you want to download hundreds of megabytes as a response to a web request anyway?

---

### Post by indytim on 2011-05-26
If the problem is on your server end, you could try modifying some of the settings in your php,ini file (this will require a restart of Apache to become effective).  Here are a few reas that merit your attention:

```

; Maximum time (in seconds) for connect timeout. -1 means no limit
mysql.connect_timeout = 60

; Maximum allowed size for uploaded files.
upload_max_filesize = 12M


max_execution_time = 300     ; Maximum execution time of each script, in seconds

max_input_time = 600 ; Maximum amount of time each script may spend parsing request data


memory_limit = 64M      ; Maximum amount of memory a script may consume (16MB)




```

Hope this helps.

IndyTim / DataMan

---

