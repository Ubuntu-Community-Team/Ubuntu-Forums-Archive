---
title: "javascript direct page to servlet from servlet"
date: 2011-05-29
forum: Programming Talk
---

### Post by badperson on 2011-05-29
Hi,

I have a servlet page that allows the user to perform some admin functions. One is a function that will delete the data in a database.

I would like to have a javascript confirmation dialog that sends the request to go to the new servlet only if the user confirms...

what would go in here to make that happen? 

```

if (confirm("Your question)) { 
 // do things if OK
}
```

tried some searching, but the examples I saw were all jsp pages. (I suppose I could just re-write the servlet as jsp)

thanks, 
bp

---

### Post by Some Penguin on 2011-05-29
You can use JavaScript to pop up a form with an "are you really sure" message, a submit input (renamed "Go ahead, unmake my data" or however you like :P) and a button ('cancel') which uses a bit of JavaScript to close the form window.  The form's 'action' field points to the servlet you wish to call.

---

