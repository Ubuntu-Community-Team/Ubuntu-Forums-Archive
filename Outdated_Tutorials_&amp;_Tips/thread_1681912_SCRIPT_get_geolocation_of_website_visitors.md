---
title: "SCRIPT: get geolocation of website visitors"
date: 2011-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by wltj on 2011-02-05
Hello Ubuntu-ers. Here's a little script based on [this]("http://www.commandlinefu.com/commands/view/1205/find-geographical-location-of-an-ip-address") command from commandlinefu.com.

The script will extract IPs from an apache logfile and run them through a location lookup service so you can see where your website visitors are goegraphically coming from. It outputs an html page like [this]("http://www.jrepo.org/pgs/2011-02-02_visitors.html"). You can easily change the formatting to suit your style.

Just set variables before running. You have the option of connecting to your web server over ssh to download the log file or run it on a log already on your comp. Set threshold so you only see visitors who appear in your logs X amount of times or more to avoid overloading the server that does the lookups and get blacklisted. You can basically run this on any list of IPs in a file. Hope its useful. ;)

```

#!/bin/bash
# 2011-02-02
# If you use this or can improve it in any way, or have problems running it please email joe at jrepo.org, or leave a comment at http://www.jrepo.org/wp/geolocation-ip-lookup-script -- Thanks!
# if you have a bunch of blank entries in html output, your lookups were blocked. (see modulus if/else)
# REQS (commands used in script): perl, grep, sed, awk, wget...
#
############################# set variables #############################

THRESHOLD=10; # dont lookup geolocation unless this many hits from specific IP
DATE=$(date +%F) 
HTML_OUTFILE=""$HOME"/"$DATE"_visitors.html" # save html output

USE_SCP="false"
# if true, fill SCP_ variables below. If false, set LOC_LOGFILE in else clause.

if [ "$USE_SCP" == "true" ]; then
  SCP_USER=""
  SCP_HOST=""
  SCP_PORT="22"
  SCP_LOGDIR="" # apache log directory, no trailing '/'
  SCP_LOGFILE="access.log" # apache log filename
  RM_LOGFILE="true" # set to true if you want to remove local copy of log after IP lookups finish.
else  
  # if not retrieving log from remote server, point below to your local apache log file.
  LOC_LOGFILE="/var/log/apache2/access.log"
fi

############################ start output #############################

if [ "$USE_SCP" == "true" ]; then
  # Retrieve apache log from server
  scp -P "$SCP_PORT" "$SCP_USER"@"$SCP_HOST":"$SCP_LOGDIR"/"$SCP_LOGFILE" ./
  if [ -s ./"$SCP_LOGFILE" ]; then
    LOC_LOGFILE="./"$SCP_LOGFILE"" # don't change
  else
    echo "There was a problem retrieving "$SCP_LOGFILE" from "$SCP_HOST"."
    exit 1;
  fi
else
  if [ ! -s "$LOC_LOGFILE" ]; then
    echo ""$LOC_LOGFILE" doesn't exist, please check LOC_LOGFILE variable in script." 
  fi
fi
fname=$(basename "$LOC_LOGFILE")

# start html.
echo -e "<html><head>\n<style type=\"text/css\">\nbody{color: black; background-color: white; }\np.times{ font-size: .8em; }\nh2{ font-size: 1.4em; font-weight: bold; text-align: center; }\ntable{ padding: 4px; border: solid thin black; }\ntr{ border: solid thin black; }\ntd.ip{ background-color: grey; font-weight: bold; color: navy; text-align: center; }\ntd.one{ background-color: silver; font-weight: bold; text-align: right; padding-left: 5px; padding-right: 5px; border: solid thin black; }\ntd.two{ background-color: silver; text-align: left; padding-left: 5px; padding-right: 5px; border: solid thin black; }\n</style>\n<title>Apache "$fname" Visitor Location Data</title>\n</head>\n<body>\n<h2>"$DATE": Apache "$fname" Visitor Location Data</h2><hr />\n<p class=\"times\">started: $(date +%r) || <font color=\"red\">Threshold: "$THRESHOLD"</font></p>\n<table>" > "$HTML_OUTFILE"

subthresh="0"; # count number of IPs that aren't processed b/c below threshold.
count="4" # use in modulus calcs
# get unique IPs from log
for IP in $( awk {'print $1'} "$LOC_LOGFILE" | sort -n | uniq ); do
  # count number of times IP shows in log

  hits=$( grep "$IP" "$LOC_LOGFILE" | wc -l )
  if [ "$hits" -lt "$THRESHOLD" ]; then
    ((subthresh++))
  else
    # modulus if/else
    # switch user agent string and wait time depending on modulus values
    # so hopefully geolocation server doesn't know we're scraping.
    # try setting higher TIMEWAIT values if you are blocked.

    mod1=$( expr "$count" % 3 )
    if [ "$mod1" -eq 0 ]; then
      USERAGENT="Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.9) Gecko/20100915 Gentoo Firefox/3.6.9"
    elif [ "$mod1" -eq 1 ]; then
      USERAGENT="Mozilla/5.0 (Windows; U; MSIE 9.0; WIndows NT 9.0; en-US)"
    else # modulus equals 2
      USERAGENT="Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/534.17 (KHTML, like Gecko) Chrome/11.0.655.0 Safari/534.17"
    fi

    mod2=$( expr "$count" % 4 )
    if [ "$mod2" -eq 0 ]; then
      TIMEWAIT="1"
    elif [ "$mod2" -eq 1 ]; then
       TIMEWAIT="4"
    elif [ "$mod2" -eq 2 ]; then
      TIMEWAIT="3"
    else # modulus equals 3
      TIMEWAIT="2"
    fi
    ((count++))
    echo "<tr><td class=\"ip\" colspan=\"2\">"$IP" logfile hits: <font color=\"yellow\">"$hits"</font></td></tr>" >> "$HTML_OUTFILE";
    # wget's -w (--wait) option wasn't working for me so we'll use sleep instead...
    sleep "$TIMEWAIT"
    # get location data and write to html
    wgetdata=$(wget -U "$USERAGENT" "$TIMEWAIT" -qO- http://whatismyipaddress.com/ip/"$IP" | grep -Eo "Hostname:>[^<]*|ISP:</th><td>[^<]*|Country:</th><td>[^<]*|State/Region:</th><td>[^<]*|City:</th><td>[^<]*" | perl -pi -e 's!^(.+):(</th><td>)(.+)$!<tr><td class=\"one\">$1:</td><td class=\"two\">$3</td></tr>!gi') 
    if [ "$wgetdata" != "" ]; then
      echo "$wgetdata" >> "$HTML_OUTFILE";
      echo "Success: "$IP""
    else
      echo "Fail: wget did not return data for "$IP""
    fi  
  fi
done;

# end html.
echo -e "</table>\n<p class=\"times\">finished: $(date +%r) || <font color=\"red\">"$subthresh" IPs were below the threshold.</font></p>\n<hr />\n</body>\n</html>" >> "$HTML_OUTFILE"
if [ "$USE_SCP" == "true" ]; then
  if [ "$RM_LOGFILE" == "true" ]; then rm "$LOC_LOGFILE"; fi
  unset SCP_USER SCP_HOST SCP_PORT SCP_LOGDIR SCP_LOGFILE RM_LOGFILE
fi

unset DATE HTML_OUTFILE LOC_LOGFILE IP TIMEWAIT USERAGENT subthresh count hits mod1 mod2
exit 0;
```

---

