---
title: "[PHP / AJAX] Simultaneous AJAX requests"
date: 2009-05-06
forum: Programming Talk
---

### Post by smani on 2009-05-06
Hello.
I am trying to make two AJAX requests work simultaneously, a very simplified code is the following:
Server side:
```

session_start();

function abort(){
    $_SESSION['abort']=true;
}

function someTask(){
    while(workToDo=true && $_SESSION['abort']==false){
        do_some_task();
    }
}

```
Client side:
```

<script type="text/javascript">

new AJAXRequest().GET('page.php?task=someTask',callbackfz);
abortBtn.onclick=function(){
new AJAXRequest().GET('page.php?task=abort',callbackfz);
}
</script>

```

Now, it seems as if the webserver only processes the requests sequentially, i.e. the abort request is only processed once the someTask request has completed... Firefox should allow up to 6 simultaneous http connections with a server, is it therefore a problem/limitation with apache / php ? Also I was wondering, should the AJAX calls be indeed processed simultaneously, are session variables dynamic inside the php instance? I.e. if another instance changes a session variable, will it also be changed immediately in any other running instance?

Thanks for any inputs!
smani

---

### Post by DocForbin on 2009-05-06
Pretty sure the session thing isn't going to work for the reason you already suspect. You could set a flag in a database or write a temp file to check for (then delete the file after the do work loop).

---

### Post by DocForbin on 2009-05-06
or write the temp file first, add a check for it in your loop, and delete it in your abort function.

---

### Post by smani on 2009-05-06
Thanks for your answer! That issue seems tackable, though I am still in the dark on why the requests are processed serially. :S

---

### Post by DocForbin on 2009-05-06
what makes you think they are?

---

### Post by smani on 2009-05-06
My complete abort function is the following:
```

if($task=="abort"){
    $taskID=$_GET['taskID'];
    if(!isset($_SESSION["t$taskID"])){echo "0\nThe specified operation does not exist";}
    else if($_SESSION["t$taskID"]['working']!=true){unset($_SESSION["t$taskID"]);echo "0\n";}
    else{
        $_SESSION["t$taskID"]['aborted']=true;
        $timeout=0;    // timeout for 15 seconds
        while($_SESSION["t$taskID"]['working']==true && $timeout<15){
            sleep(1);
            ++$timeout;}
        if($timeout==15){echo "51\nTimeout trying to abort task.";}
        else{
            unset($_SESSION["t$taskID"]);
            echo "0\n";}}
    exit(0);
}

```

If I look at the return text, I get "The specified operation does not exist", which can only happen after the work-task has ended, as I designed tasks to work as follows:
- get a TaskID via AJAX and return it to the client:
```

if($task=="getid"){
    $taskID=rand();
    while(isset($_SESSION["t$taskID"])){$taskID=rand();}
    $_SESSION["t$taskID"]['aborted']=false;
    $_SESSION["t$taskID"]['working']=true;
    $_SESSION["t$taskID"]['completed']=0;
    echo "0\n".$taskID;
    exit(0);
}

```
- start the task itself identified by the taskID by with another AJAX request, example:
```

if($task=="sometask"){
    $taskID=$_GET['taskID'];
    $items=json_decode($_POST['items']);
    for($i=0;$i<count($items->{'items'});++$i){
        if($_SESSION["t$taskID"]['aborted']==true){$_SESSION["t$taskID"]['working']=false;echo "52\nAborted";exit(0);}
        //Some task
    }
    echo "0\n";
    unset($_SESSION["t$taskID"]);
    exit(0);
}

```
- a progess window is shown on the client side with a cancel button, which, if pressed, executes the above abort function with a separate AJAX request.
- when the task ends on server side, all session variables concerning that taskID are unset.

Therefore even if session variables were not dynamic in the sense I meant above, the taskID would exist from when the ID is created to when the task has ended, hence the only possibility I see is that the requests run sequentially. Also, if I try to load any page on the same server while the task is executing, it won't load until the task is complete.

---

### Post by DocForbin on 2009-05-06
Probably its just a problem with your code/testing, but I guess you could have the MaxClients directive set to 1 in apache.

---

### Post by smani on 2009-05-06
```

cat apache2.conf | grep Max
# MaxKeepAliveRequests: The maximum number of requests to allow
MaxKeepAliveRequests 100
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
# MaxClients: maximum number of simultaneous client connections
# MaxSpareThreads: maximum number of worker threads which are kept spare
# MaxRequestsPerChild: maximum number of requests a server process serves
    MaxClients          150
    MaxSpareThreads      75 
    MaxRequestsPerChild   0

```
Seems okay .. I'll do some more testing tomorrow, in the meantime thanks for your replies!

---

### Post by DocForbin on 2009-05-06
I haven't looked at your code, but write a test script that takes a while to finish, e.g

<?php
sleep(120);
?>

and access a 2nd test script, e.g.

<?php
phpinfo();
?> 

while the first is running. If the 2nd waits for the first to complete then it is some strange configuration issue. Otherwise the problem is your code/testing...

---

### Post by smani on 2009-05-07
Okay, got it!
Seems like session variables make AJAX request run sequentially, i.e. my test code:
Client:
```

...
<script type="text/javascript">
function AJAX1(el){
	AJAXFetch(new AJAXObj(), 'GET',true,'test.php?task=task1',null,function(text){el.value=text;});
}
function AJAX2(el){
	AJAXFetch(new AJAXObj(), 'GET',true,'test.php?task=task2',null,function(text){el.value=text;});
}
</script>
...
<input type="button" value="AJAX Request 1" onclick="AJAX1(this);"/>
<input type="button" value="AJAX Request 2" onclick="AJAX2(this);"/>

```
Server:
```

<?php
session_start();
$task=$_GET['task'];
if($task=="task1"){
	$_SESSION['test']=1;
	sleep(10);
	echo "Task 1 OK, ".$_SESSION['test'];}
else if($task=="task2"){
	$_SESSION['test']=2;
	echo "Task 2 OK, ".$_SESSION['test'];}
?>

```
Now, if I comment out the three session-related statements (session_start and the two $_SESSION['test'] assignments), the requests run in parallel as expected. As soon as there is a session related statement, they run sequentially, and the result is indeed that the variables are not synchronized, i.e. AJAX1 returns "Test 1 OK, 1", AJAX2 returns "Test 2 OK, 2".
Good news that there is an explanation, bad news because I sort of need session variables for the scripts to work, even basic ones such as $_SESSION['workdir']...

---

### Post by smani on 2009-05-07
Right, in case someone want's more info on the topic, here is a good explanation: [http://ch2.php.net/manual/en/ref.session.php#64525](http://ch2.php.net/manual/en/ref.session.php#64525)

---

