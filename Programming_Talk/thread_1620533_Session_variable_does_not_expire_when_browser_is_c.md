---
title: "Session variable does not expire when browser is closed (PHP)"
date: 2010-11-13
forum: Programming Talk
---

### Post by yc2 on 2010-11-13
Hello,

When I run this code the frist time it only prints "2: Ubuntu". Quite obviously the session varible has not been set when "1: " is printed.

However, when I close the browser, open it again and run the page again, Ubuntu is printed twice!!! _It seems the session variable is still valid after closing the browser._

Can someone please explain how this can be possible? I thought session variables expired when the browser was closed.

(My "real" problem regards logging in.)

```
<?
session_start();

echo "1: " . $_SESSION['myOS'];
echo "<br>\r\n";

$_SESSION['myOS'] = "Ubuntu";

echo "2: " . $_SESSION['myOS'];
?>
```

---

### Post by worseisworser on 2010-11-13
A session cookie (id) is stored at the client end (browser); this is used to (re-)associate the client session with the server session and its data. It has a timeout.

---

### Post by Reiger on 2010-11-13
The PHP documentation on [session_destroy]("http://www.php.net/manual/en/function.session-destroy.php") should be a good start.

---

### Post by yc2 on 2010-11-13
Thank you.

I found this, I assume it reflects the maximum length of any session, that worseisworser refers to.

session.gc_maxlifetime	1440

My first intention was to let the session die when the browser is closed. I do not think I can use session_destroy only. I could send it by AJAX on event unload. However, I have used that event before and the unload event is not reliable according to my experience. I could only use session-destroy on an intentional logout by the user, not just on browser close.

I found this on stack overflow. Sorry for not having the exact link.
```
if (isset($_SESSION['LAST_ACTIVITY']) && (time() - $_SESSION['LAST_ACTIVITY'] > 1800)) {
    // last request was more than 30 minates ago
    session_destroy();   // destroy session data in storage
    session_unset();     // unset $_SESSION variable for the runtime
}
$_SESSION['LAST_ACTIVITY'] = time(); // update last activity time stamp
```

Maybe this is the best way?

If I just use 
ini_set('session.gc_maxlifetime',14400);  // but with lower value
the user will be kicked out even if he is active.

It is not a big thing, but my first intention, to let the session die on browser close seems not to be possible?

---

### Post by yc2 on 2010-11-13
Another surprise to me was that the session variable is still present to the page that destroyed it. It will not be available to other pages though.

Running the following repeatedly will print "Ubuntu" for 2, 3, 4. But never for 1.

```
session_start();

echo "1: " . $_SESSION['myOS'];
echo "<br>\r\n";

$_SESSION['myOS'] = "Ubuntu";

echo "2: " . $_SESSION['myOS'];
echo "<br>\r\n";

session_destroy();   // destroy session data in storage
session_unset();     // unset $_SESSION variable for the runtime

echo "3: " . $_SESSION['myOS'];
echo "<br>\r\n";

sleep(10);

echo "4: " . $_SESSION['myOS'];
echo "<br>\r\n";
```

---

