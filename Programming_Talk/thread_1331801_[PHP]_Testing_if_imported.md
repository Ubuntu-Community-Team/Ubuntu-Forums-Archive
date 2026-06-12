---
title: "[PHP] Testing if imported"
date: 2009-11-19
forum: Programming Talk
---

### Post by Can+~ on 2009-11-19
In python, it's possible to add a test if the current file is being executed directly, or being imported.

[PHP]#this is B.py

def printfoo():
    print "foo"

if __name__ == "__main__":
    #run a test
    printfoo()[/PHP]

Is there any equivalent of this in PHP? I've tried looking in google, but my queries run empty (or maybe I'm not choosing the right words).

---

### Post by Slimbo on 2009-11-19
[http://php.net/manual/en/function.get-included-files.php](http://php.net/manual/en/function.get-included-files.php)
[http://php.net/manual/en/function.function-exists.php](http://php.net/manual/en/function.function-exists.php)

---

### Post by Can+~ on 2009-11-19
Maybe I should've been more explicit.

Let's say that I have A.php and B.php. A includes B.

Now, if I run A.php, it's all fine, A runs and includes the required functions from B and produces the desired output. 

But if I run B.php, i want to output a different result, something like a test-case of the particular functions defined inside B.

---

### Post by Slimbo on 2009-11-19
B.php
[php]if (basename(__FILE__, '.php') == 'B') {
    echo 'File B called directly from the address bar.';
} else {
    echo 'File B executed from within ' . __FILE__ . '.';
}
[/php]A.php
[php]include('B.php');[/php]Not entirely sure if it'll work but give it a go and let us know the outcome.

---

### Post by Reiger on 2009-11-19
Simple (once you know __FILE__ exists):
[php]
function getWorkingDir() {
    return dirname(__FILE__); # for compatibility; as of PHP 5.3 return __DIR__ should suffice
}

function configScript() {
    $pwd = getWorkingDir();
    $script = substr(__FILE__,strlen($pwd) +1);
    return $script;
}

// this function checks whether or not:
// - this script is executed directly, or included/required from elsewhere
// - this script is invoked from command line or via HTTP page request
function request() {
    $script = configScript(); // script name of this file
    if(isset($_SERVER['SCRIPT_NAME']) && strpos($_SERVER['SCRIPT_NAME'], $script) !== false) {
        if(isset($_SERVER['REQUEST_METHOD'])) {
            // from HTTP: serve the website
        }
        else {
	    // from commandline: do useful stuff if appropriate
        }
        return true;
    }
    else {
        // not executed, but included: do nothing.
        return false;
    }
}
[/php]

---

### Post by Can+~ on 2009-11-20
```
...@...:~/Desktop$ php A.php
B: I'm being imported
A: Running
...@...:~/Desktop$ php B.php
B: I'm running locally
```

Works like a charm. Thank you.

---

