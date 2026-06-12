---
title: "can you collect a value from url into javascript?"
date: 2011-01-31
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-31
I can do this using $_GET[ into PHP
What I need is the value to be used in the javascipt

So, either pass the php value into javascript or
collect the value from the url into javascript

Any ideas?
thanks for any help

---

### Post by sdowney717 on 2011-01-31
[PHP]I made it work using javascript to get the value
name this code to ubuntulist3.php
run it and it saves the position of the scrolling div when you click the links

Can someone tell me how to make this work with any scrolling divs?
right now it works for id = div1

```

<!--shows a working scrolling text window which when refreshed maintains the div1 scroll position-->

<br />



 <div id="div1"  style="overflow: auto;   margin-right:auto; float: left; margin:25px; width:540px;height:500px;background-color:aliceblue;">  
	<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 2px inset; text-align: left; ">'

#!/bin/bash 
<a href="javascript:setscroll('ubuntulist3.php')">setscroll</a>
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
<a href="javascript:setscroll('ubuntulist3.php')">setscroll</a>
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
 
    <div id="div2" style=" overflow: auto;position:absolute; left:600px; float:left; margin:25px; width:540px;height:500px;background-color:aliceblue;">	
		<pre class="alt2" dir="ltr" style="margin: 0px;	padding: 6px; border: 2px inset; text-align: left; ">'



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

		

<script type="text/javascript">
     // if query string in URL contains scroll=nnn, then scroll position will be restored
     // get query string parameter with "?"
     var search = window.location.search;
       if (search){
	  // find scroll parameter in query string
	  var matches = /div1scroll=(\d+)/.exec(search);
          // alert(matches); //119,119
          // alert(matches[1]); 119
	  if (matches) document.getElementById('div1').scrollTop= matches[1];
}
 
</script>

<script type="text/javascript">
function setscroll(href){
      var scroll = document.getElementById('div1').scrollTop;
      //document.write("<BR>scroll position of div1 = ");
      //document.write(scroll);

      //now we assign the new value to the input
      //document.getElementById("scrolls").value=scroll;	
      //and now we test the hidden value
      //alert(document.getElementById("scrolls").value)      
      //window.location.href = href;
      // set href location with scroll position parameter
      window.location.href = href + '?&div1scroll=' + scroll;
}

</script>

<a href="javascript:setscroll('ubuntulist3.php')">set div1 to desired scroll position</a>




I tried this using hidden fields but got stumped trying to take the data back into javascript, so I simply wrote the scroll into the url

<script>
var hidden=document.getElementById('myfield');
hidden.value='whatever you want'
</script>

<input type="hidden" id="myfield" name="myfield" value="" />
<input type="hidden" name = "ws1" id="scrolls" >

 

```[/PHP]

---

### Post by Reiger on 2011-01-31
Uh, if you are going to use PHP you could use PHP to setup a pre-parsed representation of the URL.
[php]
<script type="text/javascript"><![CDATA[
  function get_url_contents() {
    var props = {};
    
    <?php
    foreach($_GET as $k=>$v) {
      echo "props['$k']= '$v';",PHP_EOL;
    }
    ?>
    return props;
  }
]]></script>
[/php]

Or you could use the window.location object inside JavaScript itself. To see what it can do try this:
```

var str="window.location = {";
for(var i in window.location) {
  str += ("\n"+i + ': '+ window.location[i]);
}
alert(str + "\n};");

```

---

### Post by sdowney717 on 2011-01-31
cool, I added just to see what it outputs and the 'search' is what I am using in my current javascript

Where is a list of all these javascript commands or what do you call them? I keep seeing people using them but on the few javascript tutorials they dont mention any of them.
such as window.location.search, etc...

> 
<script type="text/javascript">
     // if query string in URL contains scroll=nnn, then scroll position will be restored
     // get query string parameter with "?"
     var search = window.location.search;
       if (search){
	  // find scroll parameter in query string
	  var matches = /div1scroll=(\d+)/.exec(search);
          // alert(matches); //119,119
          // alert(matches[1]); 119
	  if (matches) document.getElementById('div1').scrollTop= matches[1];
}
 var str="window.location = {";
for(var i in window.location) {
  str += ("\n"+i + ': '+ window.location[i]);
}
alert(str + "\n};");
</script>

<script type="text/javascript">
function setscroll(href){
      var scroll = document.getElementById('div1').scrollTop;     
      // set href location with scroll position parameter
      window.location.href = href + '?&div1scroll=' + scroll;
}

</script>

---

