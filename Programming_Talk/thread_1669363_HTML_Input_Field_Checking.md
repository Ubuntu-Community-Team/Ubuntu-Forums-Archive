---
title: "HTML Input Field Checking"
date: 2011-01-17
forum: Programming Talk
---

### Post by era86 on 2011-01-17
Greetings!

I have a situation (which is quite common) that involves checking for any changes to a given set of text inputs on a webpage.  Basically, I only want to call a web service iff the inputs on the page have been changed.  On page load, the inputs are prepopulated with text that is pulled from a database, so some fields will have values already in them.

My naive approach is to store the default values somewhere in javascript on page load and do a check on each field when the user makes the call to submit.

My other naive approach is to add an onChange, onBlur, etc. action to the inputs and set flags in javascript that will tell me whether an input is changed or not.

After googling around, I've found similar approaches to my own, but i'd like to know if anyone knows something better or if someone has ran into a similar situation.

Thanks so much!:popcorn:

---

### Post by r-senior on 2011-01-18
The drawback of using Javascript is that it can usually be disabled in the browser. For a server-side solution it depends on the language (and any frameworks used) but if we take Java as an example, a solution could go something like this:

1. Create a value object that encapsulates the values in the form:

```

public class ValueObject {
    
    private String forename;
    private String surname;

    // Getters and setters go here ...

    // Over-simplified equals method (doesn't check for null, etc)
    public boolean equals(Object o) {
        return forename.equals(o.forename) && surname.equals(o.surname);
    }

}

```

2. Store a suitable instance of the object in session scope prior to loading the form. (This could be achieved with a session listener in Java that forces an instance into session scope when a new session is created).

3. Populate the form from the value object in session scope.

4. When the values are submitted, assemble the submitted value object from the request parameters and compare to the object in session scope:

```

    ValueObject posted = new ValueObject();
    posted.setForename(request.getParameter("forename");
    posted.setSurname(request.getParameter("surname");
    
    if (!posted.equals(session.getAttribute("USER_DETAILS")) {
        callMyWebService(posted);
    }

```

Server-side sessions time out of course, so that needs to be handled as you see fit.

---

### Post by v8YKxgHe on 2011-01-18
Very simple with jQuery, [http://jquery.com](http://jquery.com) e.g.:

```
$(document).ready(function() {
    $(":input").change(function() {
        alert("changed!");
    });
});
```

---

### Post by worksofcraft on 2011-01-18
As has been said, people can have client side scripting disabled and also people can interfere with the Javacode to bypass any client side security.

It doesn't really matter which approach you use, the Java script form validation can never be more than just an aid to reduce server load and assist bona-fide web site visitors.

---

