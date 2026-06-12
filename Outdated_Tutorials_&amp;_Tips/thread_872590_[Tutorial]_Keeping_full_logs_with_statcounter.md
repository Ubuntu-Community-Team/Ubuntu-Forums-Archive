---
title: "[Tutorial] Keeping full logs with statcounter"
date: 2008-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by pabix on 2008-07-28
Hello!
If you use statcounter for your web site, you may have noticed that they only keep 500 lines of logs.
If you want to keep your *full logs* and not to connect everyday to statcounter to download the CSV file, here is a script that you can put into your crontab (look for it), and henceforth it will fetch your logs whenever you want, without prompting anything to you.
All you have to do is:
[LIST]
[*]Put this file in ist own directory, to avoid overwriting files
[*]Make it executable
[*]Edit lines 2, 3 and 4. To know the project number, you may have to go to statcounter.com a last time and move your mouse cursor over the link to your project's stats.
[*]Run it **from its own directory** (otherwise it could overwrite other files).
[/LIST]
You will afterwards find a file called “logs”, **do not rename it**, because it will be grown everytime you run the script (if there has been some new visit on your web site).

I will not provide any warranty but I will try to maintain it on [this page]("http://forum.ubuntu-fr.org/viewtopic.php?id=239874").

```
#!/bin/bash
USERNAME="your user name"
PASSWORD="your password"
PROJECT_ID="the project number in statcounter"

Custom_headers="User-Agent: Netcat/Log Fetcher Bot
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: fr,fr-fr;q=0.8,en-us;q=0.5,en;q=0.3
Accept-Encoding: deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7"

# Getting www.statcounter.com {{{

nc www.statcounter.com 80 > RECEIVED << EOF
GET / HTTP/1.0
Host: www.statcounter.com
${Custom_headers}

EOF

# }}}
# getting session id {{{

CONNEXION_SERVER="$(grep 'method="POST"' RECEIVED | grep -o 'action="[^"]*"' | grep -o "[a-z]*[0-9]*.statcounter.com")"
URL="$(grep "counter.php" RECEIVED | grep -o "http://[a-z]*[0-9]*.statcounter.com/counter.php.*invisible=0")"
SERVER="$(echo "$URL" | grep -o "[a-z]*[0-9]*.statcounter.com")"
PAGE="$(echo "$URL" | grep -o "/counter.php?.*")"
nc "$SERVER" 80 > RECEIVED << EOF
GET ${PAGE} HTTP/1.0
Host: ${SERVER}
${Custom_headers}

EOF
FIRST_COOKIE="$(grep --binary-files=text Set-Cookie RECEIVED | grep -o "session_[^;]*;" | grep -o "[^;]*")"

# }}}
# {{{ Sending Username and Password
TO_BE_POSTED="form_user=${USERNAME}&form_pass=${PASSWORD}&remember=1&LOGIN_BUTTON=LOGIN"
LENGTH=${#TO_BE_POSTED}
nc "${CONNEXION_SERVER}" 80 > RECEIVED << EOF
POST /project/ HTTP/1.0
Host: ${CONNEXION_SERVER}
${Custom_headers}
Referer: http://www.statcounter.com/
Cookie: ${FIRST_COOKIE}
Content-Type: application/x-www-form-urlencoded
Content-length: ${LENGTH}

${TO_BE_POSTED}
EOF
# }}}

# {{{ Being redirected and changing session id
COOKIE="$(grep Set-Cookie RECEIVED | awk '{print $2}' | tr -d '\n') ${FIRST_COOKIE}"
CONNEXION_SERVER="$(grep "^Location:" RECEIVED | grep -o "[a-z]*[0-9]*\.statcounter\.com")"
NEWURL="$(grep "^Location:" RECEIVED | grep -o "/project/[^#]*")"

nc "${CONNEXION_SERVER}" 80 > RECEIVED << EOF
GET ${NEWURL} HTTP/1.0
Host: ${CONNEXION_SERVER}
${Custom_headers}
Referer: http://www.statcounter.com/
Cookie: ${COOKIE}

EOF

# }}}
# {{{ Asking for logs

nc "${CONNEXION_SERVER}" 80 > TempLOG << EOF
GET /project/standard2/csv/download_log_file.php?project_id=${PROJECT_ID} HTTP/1.0
Host: ${CONNEXION_SERVER}
${Custom_headers}
Cookie:${COOKIE}

EOF

# }}}

# {{{ Formatting log and wiping

tr -d '\r' < TempLOG | awk '/^$/ { f=1; next; } f' | sed -e 's/","/\t/g ;s/^"//g ; s/"$//g'> new_log
touch logs ; sort -r new_log logs | uniq > Complete_logs
mv Complete_logs logs
rm TempLOG
rm RECEIVED
rm new_log

# }}}

```

---

### Post by jpeddicord on 2008-07-29
Moved to server platforms: scripted; offsite link.

Edit: second thought, looks comprehensive enough from post content to be in Tutorials and Tips. Moved back. :-P

---

