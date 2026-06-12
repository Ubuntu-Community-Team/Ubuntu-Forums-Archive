---
title: "How to keep &lt;div&gt; elements lined up when increasing screen size?"
date: 2011-01-29
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-29
I notice if you hold cntrl and roll the mouse, it increases everything and if you have elements on the page they fall below each other. I want to keep them on the same row and have scroll bars appear at the page bottom when that happens.

---

### Post by worksofcraft on 2011-01-29
> **sdowney717 said:**
> I notice if you hold cntrl and roll the mouse, it increases everything and if you have elements on the page they fall below each other. I want to keep them on the same row and have scroll bars appear at the page bottom when that happens.

My web pages have a <div> with id="outer" that contains all the other bits. Then in my CSS I set the following:
```

#outer { width:56em; margin-left: auto; margin-right:auto; }

```

Then it gives me a fixed width for the text inside the outer div and I can set width of inner divs and other things using a percentage.

---

### Post by sdowney717 on 2011-01-29
If you load this as a php page and enlarge the screen, you will see the top 2 div's rollunder but the bottom 2 div's just stay in line.

I managed to figure out the div scroll position recovery when used on the top set of div, but on the bottom set which stay inline, this script wont work.


[http://scripterlative.com/files/recoverdivscroll.htm](http://scripterlative.com/files/recoverdivscroll.htm)



```
<div id="scrollArea onscroll="javascript:setScroll(this);" runat="server" style="overflow: auto;   margin-right:auto; float: left; margin:25px; width:540px;height:500px;background-color:#00f;color:#fff">
    <div  class="smallfont" style="margin-bottom:2px">Code:</div>
	<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 40px inset; text-align: left; ">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
<?php
echo '<BR>one'.time();
echo '<BR>two'.time();
echo '<BR>three'.time();
echo '<BR>four'.time();
echo '<BR>five'.time();
echo '<BR>six'.time().'<BR>';
//echo ' <a href="javascript:my_href(\'ubuntulist.php?page=10&id='0'\')">jeeeeeeeeeee</a>';
$page_num = 10;
$row = 5;


echo  '<a href="ubuntulist2.php">Reload</a><br>';
 

?> 


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>



	
 <div id='div2' style="overflow: auto;  margin-right:9999px; float: left; margin:25px; margin-right:auto; width:540px;height:500px;background-color:#00f;color:#fff">
    <div  class="smallfont" style="margin-bottom:2px">Code:</div>
	<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 40px inset; text-align: left; ">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use



c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

<?php
echo '<BR>one'.time();
echo '<BR>two'.time();
echo '<BR>three'.time();
echo '<BR>four'.time();
echo '<BR>five'.time();
echo '<BR>six'.time().'<BR>';


echo  '<a href="ubuntulist2.php"> jhkhkjhkjh </a>';


?> 

<a href="mysearch2.php?page='.$page_num.'&id='.$row[0]">'.$row[1].'</a>
until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>

<!-- reset div's so new div's start at left again  -->
<div style="clear: both;"> </div>




<?php
echo '<BR>one'.time();
echo '<BR>two'.time();
echo '<BR>three'.time();
echo '<BR>four'.time();
echo '<BR>five'.time();
echo '<BR>six'.time().'<BR>';
//echo ' <a href="javascript:my_href(\'ubuntulist.php?page=10&id='0'\')">jeeeeeeeeeee</a>';
$page_num = 10;
$row = 5;


echo  '<a href="ubuntulist2.php">Reload</a><br>';
 

?> 



</pre>
  </div>


<!--shows a working scrolling text window -->

<br />
<script type="text/javascript" src="scrollsaver.min.js"></script>

<!--<div id='div1'  "style="overflow: scroll; float: left; margin:10px; width: 550px;height: 500px;margin-right: 5px;">-->
   <div id='div1' style="float: left; margin:10px; width: 550px; ">
	<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 1px inset; width: 550px; height: 490px; text-align: left; overflow: auto">

#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div>

		<!-- / message -->
<!-- <div id='div2' style="overflow: scroll; float: left; margin:10px; width: 200px; margin-right: 5px;">-->
		
     <div id='div2' style="float: left; margin:10px; width: 0px; ">	
        <pre class="alt2" dir="ltr" style=" margin: 0px; padding: 6px; border: 1px inset; width: 550px; height: 490px; text-align: left; overflow: auto">
#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

###########################################################8
888888888888888888888888888888888888888888888888888888888888888
88888888888888888888888888888888888888888888##
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 
 <a href=ubuntulist3.php >testtttttttttttttttttttttt</a>
#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div>

<!-- reset div's so new div's start at left again  -->
<div style="clear: both;"> </div>
 <a href=ubuntulist3.php >testtttttttttttttttttttttt</a>
		<!-- / message -->
```

---

### Post by sdowney717 on 2011-01-30
so what I want is too keep the 2 div's side by side  when the screen changes, and be able to recover the scroll so the left div goes back to where it was on a post back. So far I cant do both

---

### Post by sdowney717 on 2011-01-30
I think I solved it using the absolute position tag on div2
>  <div id='div2' style="overflow: auto;  position:absolute;left:600px; width:540px; float: left; margin:25px; margin-right:auto; height:500px;background-color:aliceblue;">


now it stays lined up and the width and height settings are in the div line so I think the recoverscrolldiv javascript will work.
```


<div id="div1"  style="overflow: auto;   margin-right:auto; float: left; margin:25px; width:540px;height:500px;background-color:aliceblue;">
    <div  class="smallfont" style="margin-bottom:2px">Code:</div>
	<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 2px inset; text-align: left; ">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
<?php
echo '<BR>one'.time();
echo '<BR>two'.time();
echo '<BR>three'.time();
echo '<BR>four'.time();
echo '<BR>five'.time();
echo '<BR>six'.time().'<BR>';
//echo ' <a href="javascript:my_href(\'ubuntulist.php?page=10&id='0'\')">jeeeeeeeeeee</a>';
$page_num = 10;
$row = 5;


echo  '<a href="load.php">Reload</a><br>';
 

?> 


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>


 
	
 <div id='div2' style="overflow: auto;  position:absolute;left:600px; width:540px; float: left; margin:25px; margin-right:auto; height:500px;background-color:aliceblue;">
    <div  class="smallfont" style="margin-bottom:2px">Code:</div>
	<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 2px inset; text-align: left; ">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use



c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

<?php
echo '<BR>one'.time();
echo '<BR>two'.time();
echo '<BR>three'.time();
echo '<BR>four'.time();
echo '<BR>five'.time();
echo '<BR>six'.time().'<BR>';


echo  '<a href="ubuntulist2.php"> jhkhkjhkjh </a>';


?> 

<a href="mysearch2.php?page='.$page_num.'&id='.$row[0]">'.$row[1].'</a>
until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>


<!-- reset div's so new div's start at left again  -->
<div style="clear: both;"> </div>




<?php
echo '<BR>one'.time();
echo '<BR>two'.time();
echo '<BR>three'.time();
echo '<BR>four'.time();
echo '<BR>five'.time();
echo '<BR>six'.time().'<BR>';
//echo ' <a href="javascript:my_href(\'ubuntulist.php?page=10&id='0'\')">jeeeeeeeeeee</a>';
$page_num = 10;
$row = 5;


echo  '<a href="ubuntulist2.php">Reload</a><br>';
 

?> 



</pre>
  </div>


<!--shows a working scrolling text window -->

<br />
<script type="text/javascript" src="scrollsaver.min.js"></script>

<!--<div id='div3'  "style="overflow: scroll; float: left; margin:10px; width: 550px;height: 500px;margin-right: 5px;">-->
   <div id='div1' style="float: left; margin:10px; width: 550px; ">
	<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 1px inset; width: 550px; height: 490px; text-align: left; overflow: auto">

#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div>

		<!-- / message -->
<!-- <div id='div4' style="overflow: scroll; float: left; margin:10px; width: 200px; margin-right: 5px;">-->
		
     <div id='div2' style="float: left; margin:10px; width: 0px; ">	
        <pre class="alt2" dir="ltr" style=" margin: 0px; padding: 6px; border: 1px inset; width: 550px; height: 490px; text-align: left; overflow: auto">
#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

###########################################################8
888888888888888888888888888888888888888888888888888888888888888
88888888888888888888888888888888888888888888##
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 
 <a href=ubuntulist3.php >testtttttttttttttttttttttt</a>
#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div>

<!-- reset div's so new div's start at left again  -->
<div style="clear: both;"> </div>
 <a href=ubuntulist3.php >testtttttttttttttttttttttt</a>
		<!-- / message -->
```

---

