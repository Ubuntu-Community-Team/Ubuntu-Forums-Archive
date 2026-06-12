---
title: "ajax and nested &lt;div&gt;"
date: 2008-03-23
forum: Programming Talk
---

### Post by Elisei on 2008-03-23
hello people!! it is that time of day again for me to seek your help !

i have a problem with nested divs. Basically i have a script that uses XMLHttpRequest to set one div to display content of another html file
that it gets onClick(). That other html file also has a <div> and a component that does something else on its own onClick();

Although the first <div> does display the content of the page, the component on that page does not work, it gives me an error that 'Object is missing';  
 does anyone know how to set up nested divs with ajax?

---

### Post by lnostdal on 2008-03-23
here is how i do this using SymbolicWeb(#1):
```

(defun elisei ()
  (setf (attribute "innerHTML" :of :#body)
        (who (:div :id "content"
               (:input :type :button :id "first-button" :value "first-button")
               (:div :id "inner-div"
                 "initial content of `inner-div'"))))

  (bind :first-button "click"
        (iambda ()
          (setf (attribute "innerHTML" :of :inner-div)
                (who (:input :type :button :id "second-button" :value "second-button")))
          (bind :second-button "click"
                (iambda ()
                  (setf (attribute "innerHTML" :of :inner-div)
                        "content of `inner-div' after `second-button' has been clicked"))))))

```

i first set the innerHTML of the tag `body' to contain a button "first-button", and a div with an id `inner-div' that has some initial text in it

then i bind the event "click" of the element `first-button' to code that does _two_ things:

* sets the innerHTML of the tag `inner-div' to contain a button "second-button" 

..and..

* bind the event "click" of the element `second-button' to code that sets the innerHTML of the tag `inner-div' to the text "content of `inner-div' after `second-button' has been clicked"


i'm not 100% certain based on the little information you provide, but that last point might be what you are forgetting to do.. after loading new content you have got to (re-)setup event handlers for that content

this is probably mentioned many places, but the FAQ of jQuery talks about it:
[http://docs.jquery.com/Frequently_Asked_Questions#Why_do_my_events_stop_working_after_an_Ajax_request.3F](http://docs.jquery.com/Frequently_Asked_Questions#Why_do_my_events_stop_working_after_an_Ajax_request.3F)

edit: by the way; have you tried using Firebug to get more information about the error? [http://www.getfirebug.com/](http://www.getfirebug.com/)

#1: SymbolicWeb hasn't been released yet .. you can subscribe to this thread if you are curios: [http://ubuntuforums.org/showthread.php?t=724373](http://ubuntuforums.org/showthread.php?t=724373) .. PS: the example in this post only show off the low-level API of the library

---

### Post by wrightee on 2008-03-24
I'm not completely sure I understand the question - but for me the answer is always to use jquery :) 

$("#target_div").load("/source_page.htm #source_div")

..will get #source_div from source_page.htm and replace the content of #target_div

You could then manually bind whatever event / object you wanted in the new content of #target_div

$("#target_div a").bind("click",function(){alert("blah")})

---

