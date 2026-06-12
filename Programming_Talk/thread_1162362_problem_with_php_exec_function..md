---
title: "problem with php exec function."
date: 2009-05-17
forum: Programming Talk
---

### Post by MadnessRed on 2009-05-17
I am making  a basic php page to output info about my computer, this is mainly just to learn the exec function. Anyway, below is my code...

[PHP]<?php

function idstring($id,$decimal=false){  //MadnessRed function
	if($decimal){$d = '.'; }
	return (ereg_replace("[^0-9".$d."]", "", $id) * 1);
}
/*
Adapter 0 - ATI Radeon HD 3850
            Sensor 0: Temperature - 48.00 C
*/

$cpu = idstring(exec("more /proc/acpi/thermal_zone/THRM/temperature"));

$avg_cpu_use = exec("ps aux|awk 'NR > 0 { s +=$3 }; END {print s}'");

$gpu = exec("aticonfig --adapter=0 --od-gettemperature");
$gpu = explode(":",$gpu); $gpu = idstring($gpu[1],true)*1;

$uptime = exec("uptime");
$uptime = explode(",",$uptime);
$users = idstring($uptime[1]);
$uptime = explode("up ",$uptime[0]);
$uptime = explode(":",$uptime[1]);
if(sizeof($uptime) <= 1){
	$uptime = array(0 => 0,1 => idstring($uptime[0]));
}


echo "My computer, currently ".$cpu."&deg;C. Graphcis card is at ".$gpu."&deg;C.<br /><br />";
echo "Average use: ".$avg_cpu_use."%<br /><br />";
echo "Computer has been on for ".(idstring($uptime[0]) * 1)." hours and ".(idstring($uptime[1]) * 1)." minutes.<br /><br />";

?>[/PHP]

... and the output ...

> My computer, currently 29°C. Graphcis card is at 0°C.

Average use: 24.9%

Computer has been on for 0 hours and 57 minutes.

The problem is the graphics. They are not at zero degress. If I make a new file

[PHP]<?php echo exec("aticonfig --adapter=0 --od-gettemperature"); ?>[/PHP]

Then I get a blank output, if I do a copy paste into terminal I get this.
```
madnessred@Anthony-PC:~$ aticonfig --adapter=0 --od-gettemperature

Adapter 0 - ATI Radeon HD 3850
            Sensor 0: Temperature - 48.00 C
```

So any ideas why it isn't working?

---

### Post by Reiger on 2009-05-17
Perhaps because the exec() function actually *returns* 0 (== false == the empty string) ? That something is written to STDOUT need not mean that it is what the process returns...

If you want that kind of output/behaviour (STDOUT as function return value) you need to use shell_exec() which behaves as if you invoked the command from the terminal.

---

### Post by MadnessRed on 2009-05-18
> **Reiger said:**
> Perhaps because the exec() function actually *returns* 0 (== false == the empty string) ? That something is written to STDOUT need not mean that it is what the process returns...

If you want that kind of output/behaviour (STDOUT as function return value) you need to use shell_exec() which behaves as if you invoked the command from the terminal.

ok that makes sence, i thought that exec returned what was show in the terminal, many thanks.

---

### Post by MadnessRed on 2009-05-19
> **Reiger said:**
> Perhaps because the exec() function actually *returns* 0 (== false == the empty string) ? That something is written to STDOUT need not mean that it is what the process returns...

If you want that kind of output/behaviour (STDOUT as function return value) you need to use shell_exec() which behaves as if you invoked the command from the terminal.

hm 
<?php echo shell_exec("aticonfig --adapter=0 --od-gettemperature"); ?>
returns blank too.

---

### Post by odyniec on 2009-05-19
Try using the full path to aticonfig (e.g., /usr/sbin/aticonfig or whatever it is). It might not be in PHP's $PATH.

---

### Post by MadnessRed on 2009-05-19
> **odyniec said:**
> Try using the full path to aticonfig (e.g., /usr/sbin/aticonfig or whatever it is). It might not be in PHP's $PATH.

[php]<?php echo shell_exec("/usr/bin/aticonfig --adapter=0 --od-gettemperature"); ?>[/php]
Returns nothing

In terminal
```
madnessred@Anthony-PC:~$ /usr/bin/aticonfig --adapter=0 --od-gettemperature

Adapter 0 - ATI Radeon HD 3850
            Sensor 0: Temperature - 49.00 C

```

---

### Post by Reiger on 2009-05-19
Hmm after reading up on exec() in the PHP manual, it appears we can try yet something more:

[php]
<?php
$out_buf = array();
$err_code= exec( 'aticonfig --adapter=0 --od-gettemperature;', &$out_buf ); // see: http://nl2.php.net/manual/en/function.exec.php
echo implode( PHP_EOL, $out_buf );
?>
[/php]

Try that as a script of its own first, see whether that helps...
EDIT: Altough it may be worth invegsigating whether or not it makes a difference in how you run the script: as root, as your normal user, or as some limited dumb user (like the anonymous apache account 'www-data').

---

### Post by odyniec on 2009-05-19
Try displaying the error output then:
[PHP]<?php echo shell_exec("/usr/bin/aticonfig --adapter=0 --od-gettemperature 2>&1"); ?>[/PHP]
Does this produce any result?

---

### Post by MadnessRed on 2009-05-19
> **Reiger said:**
> Hmm after reading up on exec() in the PHP manual, it appears we can try yet something more:

[php]
<?php
$out_buf = array();
$err_code= exec( 'aticonfig --adapter=0 --od-gettemperature;', &$out_buf ); // see: http://nl2.php.net/manual/en/function.exec.php
echo implode( PHP_EOL, $out_buf );
?>
[/php]

Try that as a script of its own first, see whether that helps...
EDIT: Altough it may be worth invegsigating whether or not it makes a difference in how you run the script: as root, as your normal user, or as some limited dumb user (like the anonymous apache account 'www-data').

nothing, emtpy array is run, i tried print_r

> **odyniec said:**
> Try displaying the error output then:
[PHP]<?php echo shell_exec("/usr/bin/aticonfig --adapter=0 --od-gettemperature 2>&1"); ?>[/PHP]
Does this produce any result?

returns

/usr/bin/aticonfig: This program must be run as root when no X server is active

---

### Post by odyniec on 2009-05-19
> **MadnessRed said:**
> returns

/usr/bin/aticonfig: This program must be run as root when no X server is active

So there's your problem -- aticonfig can't talk to the X server. I suspect PHP doesn't have the DISPLAY environment variable set, so aticonfig assumes the X server is not running.

You could try running aticonfig with an explicit setting of DISPLAY:
[PHP]<?php echo shell_exec("DISPLAY=:0.0 /usr/bin/aticonfig --adapter=0 --od-gettemperature 2>&1"); ?>[/PHP]

However, it's not likely that a process started by PHP would be authorized to communicate with the X server, so this won't work either -- unless you disable X server access control:
```
sudo xhost +
```

---

### Post by MadnessRed on 2009-05-20
> **odyniec said:**
> So there's your problem -- aticonfig can't talk to the X server. I suspect PHP doesn't have the DISPLAY environment variable set, so aticonfig assumes the X server is not running.

You could try running aticonfig with an explicit setting of DISPLAY:
[PHP]<?php echo shell_exec("DISPLAY=:0.0 /usr/bin/aticonfig --adapter=0 --od-gettemperature 2>&1"); ?>[/PHP]

However, it's not likely that a process started by PHP would be authorized to communicate with the X server, so this won't work either -- unless you disable X server access control:
```
sudo xhost +
```

No protocol specified /usr/bin/aticonfig: This program must be run as root when no X server is active 

Nope, your code doesn't work, and also, I don't really want to risk messing things up with my computer for php's sake, I have a reasonable script now that work with ajax, and php and get fan speed, cpu useage and mobo/cpu temp. So I think I should be happy with that for now.

What would be the effects of 
```
sudo xhost +
```

---

### Post by odyniec on 2009-05-20
> **MadnessRed said:**
> What would be the effects of 
```
sudo xhost +
```

It disables X server access control, effectively allowing aticonfig to communicate with the server. See the xhost man page for more information. I don't think it would mess up anything -- anyway, you can turn access control back on with "xhost -".

---

### Post by MadnessRed on 2009-05-20
> **odyniec said:**
> It disables X server access control, effectively allowing aticonfig to communicate with the server. See the xhost man page for more information. I don't think it would mess up anything -- anyway, you can turn access control back on with "xhost -".

[img]http://madnessred.co.cc/anthony/Screenshot-9.png[/img]

:) it works. many thanks

---

