---
title: "notify-html-email.sh help"
date: 2010-09-26
forum: Programming Talk
---

### Post by FlynJets on 2010-09-26
First let me state I know nothing about programming/scripting. I'm trying to use the notify-html-email.sh script with Nagios in Ubuntu. I have all required programs installed and it is setup correctly in Nagios. Can anyone tell me if there is anything wrong with this script that would cause it to not work in Ubuntu but work in CentOS?

```

#!/bin/sh

# notify-html-email.sh v1.7
#  by mgothard
# www.NagiosExchange.org
VERSION="1.7"

# Requires the following shell commands/programs (in reference order):
#   sendmail   - or other command-line mail tool; called to actually handle sending of message
#   printf     - interpret escape characters before passing to mail system
#   date       - used to generate unique Content-ID and MIME boundary; also to convert Nagios Unix epoch timestamps to human readable
#   hostname   - used to generate unique Content-ID and MIME boundary
#   uuencode   - generates Base64 encodes of Nagios graphics
#   head       - used to cleanup uuencode output
#   tail       - used to cleanup uuencode output
#   python     - manipulate strings

# ChangeLog
# ---------
# 1.7 - Added Nagios 3.x compatibility
#     - Changed HTML to reflect Nagios 3.x format changes
#     - More Outlook 2007 rendering fixes
#     - Added checks for critical supporting programs
#     - Modified error messages to be more helpful
# 1.6 - Fixed MIME boundary problem
#     - Fixed capitalization problems with "text-transform" on some browsers
#     - Fixed compatibility issues with Microsoft Outlook 2007 (with a loss of HTML 4.01 Strict compliance)
# 1.5 - New format looks and acts more like Nagios itself
#     - HTML 4.01 Strict compliant; all tags in lower case and all parameters quoted in prep for XHTML 1.0
#     - Multipart MIME added with embedded graphics and alternate text
#     - Single HTML form modified with variables for ease in editing
#     - Lots of code changes/cleanup
#     - Corrected some timezone related bugs
#     - Added tons of comments
# 1.0 - Original HTML message generation; text/html MIME type only
#     - CSS 2.0 compliant

# Known Bugs
# ---------
# 1. May be some bash specific syntax in here.  Please report this if you find it.

# ****************************************
# Modify the following variables as needed
# ****************************************

# Full path to your mail program
MAILER=/usr/sbin/sendmail

# Any options necessary to read the FROM: and TO: fields, etc. from the input
MAILOPTS="-t"

# Full path to printf
PRINTF=/usr/bin/printf

# Full path to Nagios images directory.  Do NOT include a trailing backslash character! ('/')
IMAGES=/usr/local/nagios/share/images

# Text name for your reply-to address.  E-mail address is gleaned from Nagios config
REPLYNAME="Nagios"
REPLYADDRESS="$REPLYNAME <$NAGIOS_ADMINEMAIL>"

# Full URL to Nagios front-end.  Do NOT include a trailing backslash character! ('/')
URLPATH="http://nagios/nagios"

# Full URL to Nagios cgi-bin directory.  Do NOT include a trailing backslash character! ('/')
URLCGIBIN="$URLPATH/cgi-bin"

# Date command formating parameters used in HTML message.  Can be null, or include options, or both
#  ex: "--rfc-3389=seconds", "+%x %X"
DATEFORMAT="+%m/%d/%Y %l:%M:%S%P %Z"

# Generate unique MIME Content-ID base for multipart message
CONTENTIDBASE="`date +%s`@`hostname --fqdn`"

# MIME boundary string
MIMEBOUNDARY1="=_NextPart_`date +%s`_`hostname`_1"
MIMEBOUNDARY2="=_NextPart_`date +%s`_`hostname`_2"

# *************END MODIFY*****************

# Check for proper usage
[ $1 ] || {
    echo -e "notify-html-email.sh $VERISON\n\nHTML 4.0 notification for Nagios 3.x and 2.x\n\nUsage: notify-html-email <notification_type>\n\nOptions:"
    echo -e " notification_type\n    Must be 'host' or 'service' indicating the type of notification\n"
    echo -e "This script should be called by a Nagios e-mail notification command\nfrom /usr/local/nagios/etc/misccommands.cfg"
    echo -e "It uses the NAGIOS_* environmental variables to generate and send an HTML\nmessage to the recipient.  The format of the e-mail is customizable by\nediting this script.\n"
    exit -1
}

# Be sure minimum necessary variables are present
[ $NAGIOS_HOSTNAME ] || {
    echo -e "ERROR: Hostname not found.\n\nMaybe this script was not called from Nagios?\nDo not try to execute this script manually.\nType $0 for more info"
    exit -1
}
[ $NAGIOS_CONTACTEMAIL ] || {
    echo -e "ERROR: E-mail address not found.\n\nMaybe this script was not called from Nagios?\nDo not try to execute this script manually.\nType $0 for more info"
    exit -1
}
[ $NAGIOS_ADMINEMAIL ] || {
    echo -e "ERROR: Reply-To e-mail address not found.\n\nMaybe this script was not called from Nagios?\nDo not try to execute this script manually.\nType $0 for more info"
    exit -1
}

# For future functionaliy
#[ $NAGIOS_MAINCONFIGFILE ] || {
#    echo "ERROR: Unable to locate the main Nagios config file.  Not called from Nagios?"
#    exit -1
#}

# Check all necessary programs are present
[ -f $MAILER ] || {
        echo -e "ERROR: E-mail program $MAILER could not be found!\n\nPlease edit this script and change the MAILER variable accordingly"
        exit -1
}
[ -f $PRINTF ] || {
        echo -e "ERROR: Print formatting function $PRINTF could not be found!\n\nPlease edit this script and change the PRINTF variable accordingly"
        exit -1
}
[ -d $IMAGES ] || {
        echo -e "ERROR: Images directory $IMAGES could not be found!\n\nPlease edit this script and change the IMAGES variable accordingly"
        exit -1
}

# Generate Base64 encodings for inline graphics
UUIMGSTATUS3=`uuencode --base64 $IMAGES/status3.gif status3.gif | tail --lines=+2 | head --lines=-1`
UUIMGDISABLED=`uuencode --base64 $IMAGES/disabled.gif disabled.gif | tail --lines=+2 | head --lines=-1`
UUIMGDELAY=`uuencode --base64 $IMAGES/delay.gif delay.gif | tail --lines=+2 | head --lines=-1`
UUIMGACK=`uuencode --base64 $IMAGES/ack.gif ack.gif | tail --lines=+2 | head --lines=-1`
UUIMGDOWNTIME=`uuencode --base64 $IMAGES/downtime.gif downtime.gif | tail --lines=+2 | head --lines=-1`
UUIMGENABLED=`uuencode --base64 $IMAGES/enabled.gif enabled.gif | tail --lines=+2 | head --lines=-1`
UUIMGCOMMENT=`uuencode --base64 $IMAGES/comment.gif comment.gif | tail --lines=+2 | head --lines=-1`

# Graphics that may not be used (depends on notification type)
MIMEGRAPHICACK="--$MIMEBOUNDARY2
Content-Type: image/gif
Content-Transfer-Encoding: base64
Content-Description: Inline graphic
Content-ID: <ack.gif$CONTENTIDBASE>
Content-Location: $URLPATH/images/ack.gif
Content-Disposition: inline

$UUIMGACK"
MIMEGRAPHIC1="--$MIMEBOUNDARY2
Content-Type: image/gif
Content-Transfer-Encoding: base64
Content-Description: Inline graphic
Content-ID: <status3.gif$CONTENTIDBASE>
Content-Location: $URLPATH/images/status3.gif
Content-Disposition: inline

$UUIMGSTATUS3"
MIMEGRAPHIC2="--$MIMEBOUNDARY2
Content-Type: image/gif
Content-Transfer-Encoding: base64
Content-Description: Inline graphic
Content-ID: <enabled.gif$CONTENTIDBASE>
Content-Location: $URLPATH/images/enabled.gif
Content-Disposition: inline

$UUIMGENABLED"

# Initialize variables
FLAPPING="NO"
FLAPPINGCLASS="notflapping"

case $NAGIOS_NOTIFICATIONTYPE
in
 PROBLEM) BKCLR="F83838" ;
    case $NAGIOS_SERVICESTATE
    in
     WARNING) BKCLR="FFFF00" ;;
     UNKNOWN) BKCLR="FF9900" ;;
    esac ;;
 RECOVERY) BKCLR="33FF00" ;
    MIMEGRAPHICACK="" ;;
 ACKNOWLEDGEMENT) BKCLR="0099FF" ;
      R_SUBJECT="has been acknowledged by" ;
    STATUSACK="(Has been acknowledged)&nbsp;&nbsp;" ;
    MIMEGRAPHICACK="" ;;
 FLAPPINGSTART) BKCLR="F83838" ;
    R_SUBJECT="has started flapping" ;
    FLAPPING="YES" ;
    FLAPPINGCLASS="flapping" ;;
 FLAPPINGSTOP) BKCLR="33FF00" ;
       R_SUBJECT="is no longer flapping" ;
    MIMEGRAPHICACK="" ;;
 FLAPPINGDISABLED) BKCLR="0099FF" ;
    R_SUBJECT="was flapping and had flapping notifications disabled";
    FLAPPING="DISABLED" ;
    FLAPPINGCLASS="flapping" ;
    MIMEGRAPHICACK="" ;;
 DOWNTIMESTART) BKCLR="0099FF" ;
    R_SUBJECT="has entered scheduled downtime" ;
    MIMEGRAPHICACK="" ;;
 DOWNTIMEEND) BKCLR="0099FF" ;
    R_SUBJECT="has exited scheduled downtime" ;
    MIMEGRAPHICACK="" ;;
 DOWNTIMECANCELLED) BKCLR="0099FF" ;
    R_SUBJECT="had scheduled downtime cancelled" ;
    MIMEGRAPHICACK="" ;;
 TEST) BKCLR="FF66FF" ;
    MIMEGRAPHICACK="" ;;
 *) BKCLR="FF66FF" ;;
esac

# Host message prep
if [[ $1 == 'host' ]] ;
then {

# ---Section only used for alternative text message---
LASTHOSTDOWNTIME=`date --universal --date="1970-01-01 UTC $NAGIOS_LASTHOSTDOWN seconds"`
LASTHOSTUPTIME=`date --universal --date="1970-01-01 UTC $NAGIOS_LASTHOSTUP seconds"`
LASTHOSTUNREACHABLETIME=`date --universal --date="1970-01-01 UTC $NAGIOS_LASTHOSTUNREACHABLE seconds"`

if [[ $LASTHOSTDOWNTIME == "Thu Jan  1 00:00:00 UTC 1970" ]] ; then LASTHOSTDOWNTIME="never" ; fi
if [[ $LASTHOSTUPTIME == "Thu Jan  1 00:00:00 UTC 1970" ]] ; then LASTHOSTUPTIME="never" ; fi
if [[ $LASTHOSTUNREACHABLETIME == "Thu Jan  1 00:00:00 UTC 1970" ]] ; then LASTHOSTUNREACHABLETIME="never" ; fi

case $NAGIOS_HOSTSTATE
in
 UP) R_TIMES="Last time this host was down: $LASTHOSTDOWNTIME
    Last time this host was unreachable: $LASTHOSTUNREACHABLETIME" ;;
 DOWN | UNREACHABLE) R_TIMES="Last time this host was up: $LASTHOSTUPTIME" ;;
 *) R_TIMES="Error: Unknown host state" ;;
esac
# ---END SECTION---

# Catch for Nagios 2.x variable difference
if [[ $NAGIOS_HOSTNOTIFICATIONNUMBER == "" && $NAGIOS_NOTIFICATIONNUMBER != "" ]] ;
then {
    NAGIOS_HOSTNOTIFICATIONNUMBER=$NAGIOS_NOTIFICATIONNUMBER
};
fi

if [[ $R_SUBJECT == "" ]] ;
then {
    R_SUBJECT="is $NAGIOS_HOSTSTATE ($NAGIOS_HOSTNOTIFICATIONNUMBER)"
};
fi

if [[ $NAGIOS_NOTIFICATIONTYPE == "ACKNOWLEDGEMENT" ]] ;
then {
    R_SUBJECT="$R_SUBJECT $NAGIOS_HOSTACKAUTHOR"
    R_ACKADD="<tr class='commentOdd'>
      <td class='commentOdd'>$NAGIOS_HOSTACKAUTHOR</td>
      <td class='commentOdd'>$NAGIOS_HOSTACKCOMMENT</td>
    </tr>"
};
elif [[ $NAGIOS_NOTIFICATIONTYPE == "PROBLEM" || $NAGIOS_NOTIFICATIONTYPE == "FLAPPINGSTART" ]] ;
then {
    R_ACKCOMMAND="<tr class='command'>
                      <td><img src='cid:ack.gif$CONTENTIDBASE' class='icon' alt='Acknowledge'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=33&amp;host=$NAGIOS_HOSTNAME'>Acknowledge this host problem</a></td>
                    </tr>"
};
fi

R_SUBJECT="Nagios Host Alert - $NAGIOS_HOSTNAME $R_SUBJECT"
R_NUMBER=$NAGIOS_HOSTNOTIFICATIONNUMBER
R_DESCRIPTION=$NAGIOS_HOSTALIAS
R_NOTES=$NAGIOS_HOSTNOTES
R_STATE=$NAGIOS_HOSTSTATE
R_OUTPUT=$NAGIOS_HOSTOUTPUT
R_ATTEMPT=$NAGIOS_HOSTATTEMPT
R_PERFDATA=$NAGIOS_HOSTPERFDATA
R_DURATION=$NAGIOS_HOSTDURATION
R_LATENCY=$NAGIOS_HOSTLATENCY
R_EXECUTION=$NAGIOS_HOSTEXECUTIONTIME
R_PERCENT=$NAGIOS_HOSTPERCENTCHANGE
R_LASTCHECK=`date --date="1970-01-01 UTC $NAGIOS_LASTHOSTCHECK seconds" "$DATEFORMAT"`
R_LASTSTATECHANGE=`date --date="1970-01-01 UTC $NAGIOS_LASTHOSTSTATECHANGE seconds" "$DATEFORMAT"`
R_COMMANDTAIL="&amp;host=$NAGIOS_HOSTNAME"
R_COMMANDADD1="<tr class='command'>
                      <td><img src='cid:status3.gif$CONTENTIDBASE' class='icon' alt='map'></td>
                      <td class='command'><a href='$URLCGIBIN/statusmap.cgi?host=$NAGIOS_HOSTNAME'>Locate host on map</a></td>
                    </tr>"
R_COMMANDADD2="48"
R_COMMANDADD3="96"
R_COMMANDADD4="25"
R_COMMANDADD5="10"
R_COMMANDADD6="55"
R_COMMANDADD7="<tr class='command'>
                        <td><img src='cid:enabled.gif$CONTENTIDBASE' class='icon' alt='enabled'></td>
                        <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=28$R_COMMANDTAIL'>Enable notifications for all services on this host</a></td>
                      </tr>
                      <tr class='command'>
                        <td><img src='cid:delay.gif$CONTENTIDBASE' class='icon' alt='delay'></td>
                        <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=17$R_COMMANDTAIL'>Schedule a check of all services on this host</a></td>
                      </tr>
                      <tr class='command'>
                        <td><img src='cid:disabled.gif$CONTENTIDBASE' class='icon' alt='disabled'></td>
                        <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=16$R_COMMANDTAIL'>Disable checks of all services on this host</a></td>
                      </tr>
                      <tr class='command'>
                        <td><img src='cid:enabled.gif$CONTENTIDBASE' class='icon' alt='enabled'></td>
                        <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=15$R_COMMANDTAIL'>Enable checks of all services on this host</a></td>
                      </tr>"
R_COMMANDADD8="58"
R_COMMANDADD9="1"
};

# Service message prep
elif [[ $1 == 'service' ]] ;
then {

# ---Section only used for alterative text message---
LASTSERVICECRITICALTIME=`date --universal --date="1970-01-01 UTC $NAGIOS_LASTSERVICECRITICAL seconds"`
LASTSERVICEWARNINGTIME=`date --universal --date="1970-01-01 UTC $NAGIOS_LASTSERVICEWARNING seconds"`
LASTSERVICEOKTIME=`date --universal --date="1970-01-01 UTC $NAGIOS_LASTSERVICEOK seconds"`
LASTSERVICEUNKNOWNTIME=`date --universal --date="1970-01-01 UTC $NAGIOS_LASTSERVICEUNKNOWN seconds"`

if [[ $LASTSERVICECRITICALTIME == "Thu Jan  1 00:00:00 UTC 1970" ]] ; then LASTSERVICECRITICALTIME="never" ; fi
if [[ $LASTSERVICEWARNINGTIME == "Thu Jan  1 00:00:00 UTC 1970" ]] ; then LASTSERVICEWARNINGTIME="never" ; fi
if [[ $LASTSERVICEOKTIME == "Thu Jan  1 00:00:00 UTC 1970" ]] ; then LASTSERVICEOKTIME="never" ; fi
if [[ $LASTSERVICEUNKNOWNTIME == "Thu Jan  1 00:00:00 UTC 1970" ]] ; then LASTSERVICEUNKNOWNTIME="never" ; fi

case $NAGIOS_SERVICESTATE
in
 OK) R_TIMES="Last time this service was critical: $LASTSERVICECRITICALTIME
    Last time this service was warning: $LASTSERVICEWARNINGTIME
    Last time this service was unknown: $LASTSERVICEUNKNOWNTIME" ;;
 WARNING | UNKNOWN | CRITICAL) R_TIMES="Last time this service was ok: $LASTSERVICEOKTIME" ;;
 *) R_TIMES="Error: Unknown service state" ;;
esac
# ---END SECTION---

# Catch for Nagios 2.x variable difference
if [[ $NAGIOS_SERVICENOTIFICATIONNUMBER == "" && $NAGIOS_NOTIFICATIONNUMBER != "" ]] ;
then {
    NAGIOS_SERVICENOTIFICATIONNUMBER=$NAGIOS_NOTIFICATIONNUMBER
};
fi

if [[ $R_SUBJECT == "" ]] ;
then {
    R_SUBJECT="is $NAGIOS_SERVICESTATE ($NAGIOS_SERVICENOTIFICATIONNUMBER)"
};
fi

if [[ $NAGIOS_NOTIFICATIONTYPE == "ACKNOWLEDGEMENT" ]] ;
then {
    R_SUBJECT="$R_SUBJECT $NAGIOS_SERVICEACKAUTHOR"
    R_ACKADD="<tr class='commentOdd'>
      <td class='commentOdd'>$NAGIOS_SERVICEACKAUTHOR</td>
      <td class='commentOdd'>$NAGIOS_SERVICEACKCOMMENT</td>
    </tr>"
};
elif [[ $NAGIOS_NOTIFICATIONTYPE == "PROBLEM" || $NAGIOS_NOTIFICATIONTYPE == "FLAPPINGSTART" ]] ;
then {
    R_ACKCOMMAND="<tr class='command'>
                      <td><img src='cid:ack.gif$CONTENTIDBASE' class='icon' alt='acknowledge'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=34&amp;host=$NAGIOS_HOSTNAME&amp;service=$NAGIOS_SERVICEDESC'>Acknowledge this service problem</a></td>
                    </tr>"
};
fi

R_SUBJECT="Nagios Service Alert - $NAGIOS_SERVICEDESC on $NAGIOS_HOSTNAME $R_SUBJECT"
R_NUMBER=$NAGIOS_SERVICENOTIFICATIONNUMBER
R_DESCRIPTION=$NAGIOS_SERVICEDESC
R_STATE=$NAGIOS_SERVICESTATE
R_OUTPUT=$NAGIOS_SERVICEOUTPUT
R_ATTEMPT=$NAGIOS_SERVICEATTEMPT
R_LINKBOX_ADD="<a href='$URLCGIBIN/extinfo.cgi?type=1&amp;host=$NAGIOS_HOSTNAME'>View Information For This Host</a><br>"
R_LINKBOXLINK_ADD="&amp;service=$NAGIOS_SERVICEDESC"
R_TITLE_ADD="<div class='data'>On Host</div><div class='dataTitle'>$NAGIOS_HOSTALIAS</div>"
R_NOTES=$NAGIOS_SERVICENOTES
R_PERFDATA=$NAGIOS_SERVICEPERFDATA
R_DURATION=$NAGIOS_SERVICEDURATION
R_LATENCY=$NAGIOS_SERVICELATENCY
R_EXECUTION=$NAGIOS_SERVICEEXECUTIONTIME
R_PERCENT=$NAGIOS_SERVICEPERCENTCHANGE
R_LASTCHECK=`date --date="1970-01-01 UTC $NAGIOS_LASTSERVICECHECK seconds" "$DATEFORMAT"`
R_LASTSTATECHANGE=`date --date="1970-01-01 UTC $NAGIOS_LASTSERVICESTATECHANGE seconds" "$DATEFORMAT"`
R_COMMANDTAIL="&amp;host=$NAGIOS_HOSTNAME&amp;service=$NAGIOS_SERVICEDESC"
R_COMMANDADD2="6"
R_COMMANDADD3="7"
R_COMMANDADD4="23"
R_COMMANDADD5="9"
R_COMMANDADD6="56"
R_COMMANDADD8="60"
R_COMMANDADD9="3"
MIMEGRAPHIC1=""
MIMEGRAPHIC2=""
};

# Catch for bad argument
else {
   echo "ERROR: Invalid argument.  Must be 'host' or 'service'"
   exit -1
};
fi

# Included for browser compatability problems with CSS text-transform: capitalize
NAGIOS_NOTIFICATIONTYPE=`echo $NAGIOS_NOTIFICATIONTYPE | python -c "print raw_input().capitalize()"`
set -- `echo $1 | python -c "print raw_input().capitalize()"`

# Message generation
#  NOTE: All of the "R_" variables change when either 'host' or 'service' is selected
MSG=`echo "From: $REPLYADDRESS
Reply-To: $REPLYADDRESS
To: $NAGIOS_CONTACTALIAS <$NAGIOS_CONTACTEMAIL>
Subject: $R_SUBJECT
MIME-Version: 1.0
Content-Type: multipart/alternative; boundary=$MIMEBOUNDARY1

--$MIMEBOUNDARY1
Content-Type: text/plain; charset=us-ascii

$R_DESCRIPTION ($NAGIOS_HOSTNAME @ $NAGIOS_HOSTADDRESS) is $R_STATE,
Nagios reports: $R_OUTPUT,
This $1 has been $R_STATE for $R_ATTEMPT consecutive attempts,
$R_TIMES

--$MIMEBOUNDARY1
Content-Type: multipart/related; boundary=$MIMEBOUNDARY2; type=text/html

--$MIMEBOUNDARY2
Content-Type: text/html; charset=us-ascii
Content-Description: HTML message
Content-ID: <html$CONTENTIDBASE>

<!DOCTYPE HTML PUBLIC \"-//W3C//DTD HTML 4.01//EN\"
            \"http://www.w3.org/TR/html4/strict.dtd\">
<html>
<head>
<title>Nagios Notification</title>
<meta http-equiv='Content-Type' content='text/html; charset=us-ascii'>
<style type='text/css'>

/* Modified styles from Nagios extinfo.css style sheet */
BODY { font-family: arial,sans-serif;  background-color: white;  color: black;  font-size: 10pt; }
.linkBox { font-size: 8pt;  background-color: #DBDBDB;  padding: 1px; }
DIV.dataTitle { text-align: center;  font-weight: bold;  font-size: 12pt; }
DIV.data { text-align: center;  font-size: 12pt; }
TABLE.data { font-size: 10pt;  background-color: white;  padding: 2px; }
TH.data { font-size: 10pt;  background-color: white;  text-align: left;  background-color: #999797;  color: #DCE5C1; }
.commandTitle { text-align: center;  font-weight: bold;  font-size: 12pt; }
TABLE.command { font-size: 10pt;  background-color: #DBDBDB;  padding: 2px; }
.command { font-size: 10pt; text-align: left; }
.commentTitle { text-align: center;  font-weight: bold;  font-size: 12pt; }
TABLE.comment { font-size: 10pt;  background-color: white;  padding: 2px; }
TH.comment { font-size: 10pt;  background-color: white;  text-align: left;  background-color: #999797;  color: #DCE5C1; }
.commentOdd { font-size: 9pt;  background-color: #DBDBDB; }
.commentEven { font-size: 9pt;  background-color: #C4C2C2; }
DIV.comment,A.comment { font-size: 10pt;  background-color: white;  text-align: center; }
.notflapping { font-size: 10pt;  text-align: left;  background-color: #33FF00;  font-weight: bold; float: left; }
.flapping { font-size: 10pt;  text-align: left;  background-color: #F83838;  font-weight: bold; float: left; }
.HostUP { font-size: 10pt;  text-align: left;  background-color: #33FF00;  font-weight: bold; float: left; }
.HostDOWN { font-size: 10pt;  text-align: left;  background-color: #F83838;  font-weight: bold; float: left; }
.HostUNREACHABLE { font-size: 10pt;  text-align: left;  background-color: #F83838;  font-weight: bold; float: left; }
.ServiceOK { font-size: 10pt;  text-align: left;  background-color: #33FF00;  font-weight: bold; float: left; }
.ServiceWARNING { font-size: 10pt;  text-align: left;  background-color: #FFFF00;  font-weight: bold; float: left; }
.ServiceUNKNOWN { font-size: 10pt;  text-align: left;  background-color: #FF9900;  font-weight: bold; float: left; }
.ServiceCRITICAL { font-size: 10pt;  text-align: left;  background-color: #F83838;  font-weight: bold; float: left; }
.commandPanel { background-color: white; text-align: center; vertical-align: top; }
.commentPanel { background-color: white; text-align: center; vertical-align: top; }
.stateInfoPanel { background-color: white; vertical-align: top; }
.stateInfoTable1 { font-size: 10pt;  background-color: #DBDBDB; text-align: left; }
.dataVar { font-size: 10pt; }
.dataVal { font-size: 10pt; }
/* End Copy */

/* a { text-decoration: none; }
a:hover { text-decoration: underline; } */
h1 { font-family: Garamond,'Times New Roman',serif; text-align: center; vertical-align: bottom; text-transform: capitalize; }
span.caps { text-transform: capitalize; }
.notif { background-color: #$BKCLR; }
.address { font-size: 10.0pt; font-style: italic; }
table.center { margin-left: auto; margin-right: auto; }
.fullwidth { width: 100%; }
.border { border-style: ridge; border-width: 2px; }
.border-thick { border-style: ridge; border-width: 3px; }
.noborder { border-style: none; }
.nopad { border-spacing: 0px; padding: 0px; }
td.onethirdl { text-align: left; vertical-align: top; width: 33%; }
td.onethirdc { text-align: center; vertical-align: middle; width: 33%; }
td.onethirdr { text-align: right; vertical-align: bottom; width: 33%; }
td.rightpanel { text-align: center; vertical-align: top; }
td.vcenter { vertical-align: middle; }
img.icon { border-style: none; border-width: 0px; height: 20px; width: 20px; }

</style>
</head>
<body>
<table class='center noborder' align='center'>
  <tr>
    <td class='notif'>
        &nbsp;
    </td>
  </tr>
  <tr>
    <td>
      <h1><a href='$URLPATH'>Nagios</a> $NAGIOS_NOTIFICATIONTYPE Notification</h1>
    </td>
  </tr>
  <tr>
    <td class='notif'>
        &nbsp;
    </td>
  </tr>
</table>
<!--$NAGIOS_LONGDATETIME-->
<table class='fullwidth noborder' align='center'>
  <tr>
    <td class='onethirdl'>
      <table cellspacing='0' class='linkBox nopad border' border='2'>
        <tr>
          <td class='linkBox'>
            $R_LINKBOX_ADD
            <a href='$URLCGIBIN/status.cgi?host=$NAGIOS_HOSTNAME$R_LINKBOXLINK_ADD'>View Status Detail For This Host</a><br>
            <a href='$URLCGIBIN/history.cgi?host=$NAGIOS_HOSTNAME$R_LINKBOXLINK_ADD'>View Alert History For This <span class='caps'>$1</span></a><br>
            <a href='$URLCGIBIN/trends.cgi?host=$NAGIOS_HOSTNAME$R_LINKBOXLINK_ADD'>View Trends For This <span class='caps'>$1</span></a><br>
            <a href='$URLCGIBIN/histogram.cgi?host=$NAGIOS_HOSTNAME$R_LINKBOXLINK_ADD'>View Alert Histogram For This <span class='caps'>$1</span></a><br>
            <a href='$URLCGIBIN/avail.cgi?host=$NAGIOS_HOSTNAME$R_LINKBOXLINK_ADD&amp;show_log_entries'>View Availability Report For This <span class='caps'>$1</span></a><br>
            <a href='$URLCGIBIN/notifications.cgi?host=$NAGIOS_HOSTNAME$R_LINKBOXLINK_ADD'>View Notifications This <span class='caps'>$1</span></a>
          </td>
        </tr>
      </table>
    <td class='onethirdc'>
      <div class='data'>
        <span class='caps'>$1</span>
      </div>
      <div class='dataTitle'>
        $R_DESCRIPTION
      </div>
      $R_TITLE_ADD
      <div class='dataTitle'>
        (<a href='$URLCGIBIN/status.cgi?host=$NAGIOS_HOSTNAME'>$NAGIOS_HOSTNAME</a>)
      </div><br>
      <div class='data'>
        <a href='$NAGIOS_HOSTACTIONURL'>$NAGIOS_HOSTADDRESS</a>
      </div>
      <p>$R_NOTES</p>
    </td>
    <td class='onethirdr'>
    </td>
  </tr>
</table>
<table class='center fullwidth nopad noborder' align='center' width='100%'>
  <tr>
    <td class='stateInfoPanel'>
      <div class='dataTitle'>
        <span class='caps'>$1</span> State Information
      </div>
      <table class='center noborder' align='center'>
        <tr>
          <td>
            <table cellspacing='0' class='center nopad border' border='2' align='center'>
              <tr>
                <td class='stateInfoTable1'>
                  <table class='noborder' align='center'>
                    <tr>
                      <td class='dataVar'>Current Status:</td>
                      <td class='dataVal'>
                        <span class='$1$R_STATE'>
                          &nbsp;&nbsp;$R_STATE&nbsp;&nbsp;$STATUSACK
                        </span>
                        &nbsp;(for $R_DURATION)
                      </td>
                    </tr>
                    <tr>
                      <td class='dataVar'>Status Information:</td>
                      <td class='dataVal'>$R_OUTPUT</td>
                    </tr>
                    <!--<tr>
                      <td class='dataVar'>Performance Data:</td>
                      <td class='dataVal'>$R_PERFDATA</td>
                    </tr>-->
                    <tr>
                      <td class='dataVar'>Check attempts:</td>
                      <td class='dataVal'>$R_ATTEMPT</td>
                    </tr>
                    <tr>
                      <td class='dataVar'>Last Check Time:</td>
                      <td class='dataVal' nowrap='nowrap'>$R_LASTCHECK</td>
                    </tr>
                    <tr>
                      <td class='dataVar' nowrap='nowrap'>Check Latency / Duration:</td>
                      <td class='dataVal' nowrap='nowrap'>$R_LATENCY&nbsp;/&nbsp;$R_EXECUTION seconds</td>
                    </tr>
                    <tr>
                      <td class='dataVar'>Last State Change:</td>
                      <td class='dataVal' nowrap='nowrap'>$R_LASTSTATECHANGE</td>
                    </tr>
                    <tr>
                      <td class='dataVar'>Current Notification Number:</td>
                      <td class='dataVal'>$R_NUMBER</td>
                    </tr>
                    <tr>
                      <td class='dataVar'>Is This <span class='caps'>$1</span> Flapping?</td>
                      <td class='dataVal'>
                        <span class='$FLAPPINGCLASS'>
                          &nbsp;&nbsp;$FLAPPING&nbsp;&nbsp;
                        </span>
                        &nbsp;($R_PERCENT% state change)
                      </td>
                    </tr>
                  </table>
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
    <td class='rightpanel'>
      <table cellspacing='0' class='nopad noborder' align='center'>
        <tr>
          <td class='commandPanel'>
            <div class='commandTitle'>
              <span class='caps'>$1</span> Commands
            </div>
            <table cellspacing='0' class='command nopad border' border='2' align='center'>
              <tr>
                <td>
                  <table cellspacing='0' class='command nopad noborder' align='center'>
                    $R_COMMANDADD1
                    <tr class='command'>
                      <td><img src='cid:disabled.gif$CONTENTIDBASE' class='icon' alt='disabled'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=$R_COMMANDADD2$R_COMMANDTAIL'>Disable active checks of this $1</a></td>
                    </tr>
                    <tr class='data'>
                      <td><img src='cid:delay.gif$CONTENTIDBASE' class='icon' alt='delay'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=$R_COMMANDADD3$R_COMMANDTAIL'>Re-schedule the next check of this $1</a></td>
                    </tr>
                    $R_ACKCOMMAND
                    <tr class='command'>
                      <td><img src='cid:disabled.gif$CONTENTIDBASE' class='icon' alt='disabled'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=$R_COMMANDADD4$R_COMMANDTAIL'>Disable notifications for this $1</a></td>
                    </tr>
                    <tr class='command'>
                      <td><img src='cid:delay.gif$CONTENTIDBASE' class='icon' alt='delay'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=$R_COMMANDADD5$R_COMMANDTAIL'>Delay next $1 notification</a></td>
                    </tr>
                    <tr class='command'>
                      <td><img src='cid:downtime.gif$CONTENTIDBASE' class='icon' alt='downtime'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=$R_COMMANDADD6$R_COMMANDTAIL'>Schedule downtime for this $1</a></td>
                    </tr>
                    $R_COMMANDADD7
                    <tr class='command'>
                      <td><img src='cid:disabled.gif$CONTENTIDBASE' class='icon' alt='disabled'></td>
                      <td class='command'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=$R_COMMANDADD8$R_COMMANDTAIL'>Disable flap detection for this $1</a></td>
                    </tr>
                  </table>
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>
<table class='center' align='center'>
  <tr>
    <td colspan='2' class='commentPanel'>
      <div class='commentTitle'>
        <span class='caps'>$1</span> Comments
      </div>
      <table>
        <tr>
          <td class='vcenter'><img src='cid:comment.gif$CONTENTIDBASE' class='icon' alt='comment'></td>
          <td class='comment'><a href='$URLCGIBIN/cmd.cgi?cmd_typ=$R_COMMANDADD9$R_COMMANDTAIL' class='comment'>Add a new comment</a></td>
        </tr>
      </table>
      <table class='comment border-thick' border='3'>
        <tr class='comment'>
          <th class='comment'>Author</th>
          <th class='comment'>Comment</th>
        </tr>
        $R_ACKADD
      </table>
    </td>
  </tr>
</table>
<p class='address'>All information is the property of <a href='mailto:$REPLYADDRESS'>$REPLYNAME</a><br>
  and should be treated as confidential</p>
</body>
</html>

--$MIMEBOUNDARY2
Content-Type: image/gif
Content-Transfer-Encoding: base64
Content-Description: Inline graphic
Content-ID: <disabled.gif$CONTENTIDBASE>
Content-Location: $URLPATH/images/disabled.gif
Content-Disposition: inline

$UUIMGDISABLED

--$MIMEBOUNDARY2
Content-Type: image/gif
Content-Transfer-Encoding: base64
Content-Description: Inline graphic
Content-ID: <delay.gif$CONTENTIDBASE>
Content-Location: $URLPATH/images/delay.gif
Content-Disposition: inline

$UUIMGDELAY

--$MIMEBOUNDARY2
Content-Type: image/gif
Content-Transfer-Encoding: base64
Content-Description: Inline graphic
Content-ID: <downtime.gif$CONTENTIDBASE>
Content-Location: $URLPATH/images/downtime.gif
Content-Disposition: inline

$UUIMGDOWNTIME

--$MIMEBOUNDARY2
Content-Type: image/gif
Content-Transfer-Encoding: base64
Content-Description: Inline graphic
Content-ID: <comment.gif$CONTENTIDBASE>
Content-Location: $URLPATH/images/comment.gif
Content-Disposition: inline

$UUIMGCOMMENT

$MIMEGRAPHIC1
$MIMEGRAPHIC2
$MIMEGRAPHICACK
--$MIMEBOUNDARY2--

--$MIMEBOUNDARY1--"`

[ "$MSG" ] || {
   echo "Error generating e-mail message."
   exit -1
}

# Send the damn e-mail already!
$PRINTF "%b" "$MSG" | $MAILER $MAILOPTS

exit

```

---

### Post by gmargo on 2010-09-26
> **FlynJets said:**
> Can anyone tell me if there is anything wrong with this script that would cause it to not work in Ubuntu but work in CentOS?


CentOS uses **bash** as it's /bin/sh, while Ubuntu uses **dash** as it's /bin/sh.  So it's a fair bet that there's a bash-ism in that script somewhere.  Change the first line to "#!/bin/bash" and see if it then works.

Update: The **if** statements in the script are in a bash-only syntax with the double-bracket:
```

if [[ $1 == 'host' ]] ;

```

---

### Post by FlynJets on 2010-09-26
> CentOS uses **bash** as it's /bin/sh, while Ubuntu uses **dash**  as it's /bin/sh.  So it's a fair bet that there's a bash-ism in that  script somewhere.  Change the first line to "#!/bin/bash" and see if it  then works.Seems that was the answer. Although I'm only receiving service notifications at the moment and no host notifications. Not sure yet if that is a config issue on my part or another issue with the script. Anyways I appreciate the help!

---

