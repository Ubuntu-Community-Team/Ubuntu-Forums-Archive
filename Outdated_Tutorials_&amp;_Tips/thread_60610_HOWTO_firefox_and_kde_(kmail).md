---
title: "HOWTO: firefox and kde (kmail)"
date: 2005-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by incinerator on 2005-08-28
Firefox with its default configuration does not integrate well with kde and vice versa. Two main use cases are to be addressed here:

1.) Clicking on a email link in a webpage should create a new email with kmail.
2.) Clicking on a weblink in kmail (and other kde apps) should open and load the link into firefox.

Now the solutions:
1.) Start firefox and type the following in the url bar: **about:config**
A big table with configuration options will appear in the main browser window.
Look for the item **network.protocol-handler.external.mailto** and make sure its value is set to **true**. The value is the right most piece of text in the row for that item. Right-click on that line and select "toggle" in the pop-up menu to toggle if necessary.

Now, do a right-click again and select **New -> String**. A window will appear, asking you to set the name of the new config item, set it to **network.protocol-handler.app.mailto** and and click OK to confirm. A second window will appear to ask for the value of the config item. Type **kmail** into its text field and confirm again.

Now, if you click on an email link on a webpage (in the status bar, that is the bar at the lower end of the firefox window, you will see something like **mailto:john.doe@johndoe.net**) kmail should fire up with a new email to that address.

2.) This can be configured by changing one kde setting. Depending on the kde version you have there may be different ways to get to that kde settings window we need. 
For kde 3.4.2, click on the **System** button in the control panel, it is the one right next to the blue **[COLOR=Blue]K[/COLOR]** button in the control panel. 
A pop-up menu appears, select **Settings**. A new konqueror window will appear showing the contents of the **settings:/** directory. Select **KDE components** -> **Component Selection**. This will open the kde control center module we need, appearing in a new window.
There is a list at the left site of that window, select **Web browser** and click on the lower button in the main section of the window, named **in following browser**. The text input field below the button will become active, type **mozilla-firefox** and click the OK button to confirm the setting.

From now on, links in emails etc. should be opened in firefox.

For older kde versions (3.4.0?), or if you have the pristine kde control center installed, the **component selection** can be accessed from the kde control center in a similiar manner. 

Note: I running KDE with a German language setting and therefore the terms used may not be proper translations, please reply to this post or send me a PM if you want to make corrections. Also, you can configure 1.) to use another email client than kmail, and 2.) can be used to open another web browser, respectively.

---

### Post by a_hippie on 2006-08-14
Great info.  Just plugged it into firefox and now I can use kmail.  very nice.

Thanks!

---

### Post by MadMarv on 2007-08-07
Thank you, thank you. BTW, this works on any flavor of Ubuntu, just change the network.protocol-handler.app.mailto to point to your preferred mail program (ex /usr/bin/mozilla-thunderbird works beautifully for me.)

---

### Post by ACGarland on 2008-04-30
If you also want the "send link" menu item in firefox to utilize kmail--including using the title of the page as the subject of the email and placing the actual link into the body of the email, then one can use the [feedmua]("http://howto-pages.org/mozilla.php") perl script.

One small modification I made to the script was to escape the URI passed by firefox before processing leading to invoking kmail since otherwise the subject line might come out containing "%20" and other characters which were encoded within the URI in human-unfriendly ways.
```

#!/usr/bin/perl -w

# feedmua.pl - (c) 2003 Godwin STEWART, all rights reserved.
# Version 0.1 / 22-OCT-2003
# Released under the GNU General Public License Version 2, the terms of which
# are available here: http://www.fsf.org/licenses/gpl.html
#
# This software is provided as is, with no guarantee of merchantability or
# fitness for any purpose. Use it at your own risk.

# bail out with an error condition if nothing was passed to the script
exit(1) if ( scalar(@ARGV) < 1 );

# declare a few local variables
my ($LINK, $RECIPIENT, $CC, $BCC, $SUBJECT, $BODY) = ("", "", "", "", "", "");
my (@PARTS, $SEGMENT, $CMDLINE);

# grab the link passed to us
$LINK = $ARGV[0];

# bail out with an error condition if it doesn't begin with "mailto:"
exit(1) unless ( $LINK =~ m/^mailto\:/i );

# strip the mailto at the beginning
$LINK =~ s/^mailto\:(.*)/$1/i;

# bail out with an error condition if nothing's left
exit(1) if ( length($LINK) == 0 );

# unquote it (kmail needs this) - modification by Tony Garland
use URI::Escape;
$LINK = uri_unescape($LINK);

# What we have now is something of the form
#
#  address?variable1&variable2&variable3&...
#
# Replace the '?' with a '&' and then split the string on '&' boundaries.
$LINK =~ s/\?/&/g;
@PARTS = split("&",$LINK);

# Treat @PARTS as a stack and pop elements off it as and when.
#
# The first element should be the recipient.
$RECIPIENT = shift(@PARTS);

# bail out with an "ok" condition if this was all there was in the link
exit(0) if ( scalar(@PARTS) == 0 );

# now loop through the remaining elements parsing them until there are
# none left

while ( scalar(@PARTS) ) {

  $SEGMENT = shift(@PARTS);

  if ( $SEGMENT =~ m/^cc=/i ) {
    ( $CC = $SEGMENT ) =~ s/^cc=(.*)/$1/i;
    next;
  }
  
  if ( $SEGMENT =~ m/^bcc=/i ) {
    ( $BCC = $SEGMENT ) =~ s/^bcc=(.*)/$1/i;
    next;
  }
  
  if ( $SEGMENT =~ m/^subject=/i ) {
    ( $SUBJECT = $SEGMENT ) =~ s/^subject=(.*)/$1/i;
    next;
  }
  
  if ( $SEGMENT =~ m/^body=/i ) {
    ( $BODY = $SEGMENT ) =~ s/^body=(.*)/$1/i;
    next;
  }

}

# From here onwards, the variables $RECIPIENT, $CC, $BCC, $SUBJECT
# and $BODY contain what you'd expect them to contain. If the
# corresponding item wasn't set in the mailto: link then the
# variable contains an empty string.
#
# Now, all you have to do is build a command line which feeds these
# variables to your mailer.
#
# For example, kmail expects a command line like this:
#
# kmail --composer -c <Cc_recipients> -b <Bcc_recipients> -s <subject> --body <body> <recipient>
#
# Always enclose the values in quotes so that empty values are in fact counted as
# empty arguments rather than just skipped altogether. So your command would look
# something like this:
#
$CMDLINE = "kmail --composer -c \"$CC\" -b \"$BCC\" -s \"$SUBJECT\" --body \"$BODY\" \"$RECIPIENT\"";
#
# See http://mozex.mozdev.org/arguments.html for details of the command line arguments
# of other mailers.

# No further processing is required in this script so hand the control over
# to the mailer rather than forking and waiting.
exec $CMDLINE;



```

---

### Post by freerk on 2009-07-27
This works in firefox 2
But i can't get it done in Firefox 3
So is changed /usr/bin/evolution to /usr/bin/evolution-off
and put a symbolic link /usr/bin/evolution which is pointing to /usr/bin/mozilla-thunderbird
And in your case /usr/bin/kmail
Works!

---

