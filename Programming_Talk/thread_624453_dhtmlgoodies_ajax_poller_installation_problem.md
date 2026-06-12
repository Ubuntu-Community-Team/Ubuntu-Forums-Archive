---
title: "dhtmlgoodies ajax poller installation problem"
date: 2007-11-27
forum: Programming Talk
---

### Post by ahjin on 2007-11-27
Hello, I'm getting errors on installing dhtmlgoodies ajax poller installation problem.
I followed the exact steps from dhtmlgoodies, but the poll did not come out. It has the erroe message:
[B]".$inf["pollerTitle"]."

"; // Output poller title $resOptions = mysql_query("select * from poller_option where pollerID='$pollerId' order by pollerOrder") or die(mysql_error()); // Find poll options, i.e. radio buttons while($infOptions = mysql_fetch_array($resOptions)){ if($infOptions["defaultChecked"])$checked=" checked"; else $checked = ""; echo "
".$infOptions["optionText"]."

"; } } ?>[/B]

Can anyone please advise on this? 
Thanks

---

### Post by smartbei on 2007-11-27
Not sure exactly what the problem is, please provide the following information so we can better diagnose the problem.
[list]
[*]Create a file with the following in it: ```
<?php phpinfo(); ?>
``` Search for the line with "short_open_tag". Post the information in the grey boxes next to it. [Better yet, if this is accessable on the internet, just post a link to the file with the phpinfo()].
[*]Post the whole error message (that is not the whole thing I believe) in [ quote ] or [ code ] tags so it is easier to understand.
[/list]

---

