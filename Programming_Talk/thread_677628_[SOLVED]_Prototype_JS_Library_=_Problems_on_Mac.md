---
title: "[SOLVED] Prototype JS Library = Problems on Mac"
date: 2008-01-25
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-01-25
Hi everyone,

Unlike some of my more recent posts, this is a language I'm very familiar with, so it's not some "noob" problem.

I use the Prototype JS Library (version 1.6.0... the latest) for AJAX functionality on all my projects, but recently I received a report of a problem:

On Macs, both Firefox and Safari, I have two pages/scripts that do not work, a login and a signup.  The crucial ones, right?

It apparently *does* submit the AJAX request, and is successful, but refuses to move from a "Processing Request" statement to the next step.  You can view this at [http://www.myshoutoutloud.com/signup.php](http://www.myshoutoutloud.com/signup.php)** (make sure you let me know what username you signup as, unless it's obvious, so I can delete any extra accounts... unless you want to keep it, in which case mention that as well please)**.

This works on Firefox on Ubuntu, and both IE and FF on Vista (Safari kept crashing, so I couldn't test that on Vista).  And since it's both FF and Safari on Macs that are having the problem, it would suggest something to do with Mac architecture, rather than a specific browser.

Here's the AJAX request on the signup page, which executes:```

$('regLoc').request({
	method: 'get',
	onLoading: function() { procLoading('registerMessage'); },
	onComplete: function() { registerTrue(); },
	onSuccess: function() { registerTrue(); },
	onFailure: function() { registerFalse; }
});

```

The onLoading portion works correctly, which you will see manifested as the "Processing" part.  Here's what doesn't work:
```

function registerTrue() {
        $('regLoc').hide();
	$('registerMessage').show();
	$('registerMessage').update('<p><strong><i>Signup successful!  Please watch for the verification email.</i></strong></p>');
	$('singlecolumn').hide();
}

```

Any ideas?  The login page is basically the same issue, with a JS redirect thrown in as well.

Thanks

---

### Post by 71fnRVVm on 2008-01-25
Problem solved, thanks to "McBastard" on #prototype (irc.freenode.net).

Having both onSuccess and onComplete was causing indecision, and removing onSuccess worked.

Thanks

---

