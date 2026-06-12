---
title: "Empty HTML 4.01 form 'action' attribute - valid?"
date: 2009-08-22
forum: Programming Talk
---

### Post by v8YKxgHe on 2009-08-22
Morning,

I pretty much always give the 'action' attribute a value that I need, however I wonder if I really do need to - as I know browsers will accept a blank value. Now, looking at the RFCs and HTML 4.01 spec, it is not entirely clear if this is valid, or just a quirk that browsers have decided to do.

[http://www.w3.org/TR/html401/types.html#type-uri](http://www.w3.org/TR/html401/types.html#type-uri) states that:

> This specification uses the term URI as defined in [URI] (see also [RFC1630]).
Now, RFC1630 does not mention anything about empty URIs as being a valid URI - however, RFC2396 ([http://www.ietf.org/rfc/rfc2396.txt](http://www.ietf.org/rfc/rfc2396.txt)) *does* specify that empty URIs are valid - and even has an exception for HTML 'form element:

[quote="4.2. Same-document References"]  A URI reference that does not contain a URI is a reference to the
   current document.  In other words, an empty URI reference within a
   document is interpreted as a reference to the start of that document,
   and a reference containing only a fragment identifier is a reference
   to the identified fragment of that document.  Traversal of such a
   reference should not result in an additional retrieval action.
  [b] However, if the URI reference occurs in a context that is always
   intended to result in a new request, as in the case of HTML's FORM
   element, then an empty URI reference represents the base URI of the
   current document and should be replaced by that URI when transformed
   into a request.[/b]
[/quote]

1630 does not say an empty URI is valid, and this is what the HTML spec uses - however it also doesn't say if it is *not* valid. So I'm quite confused as to what the expected behaviour is for HTML forms. Is it safe to use an empty 'action' attribute?

---

### Post by tom66 on 2009-08-22
action, in my experience, can be empty. In which case, it refers to the current document.

---

### Post by v8YKxgHe on 2009-08-22
Thanks, though I'm aware it *can* be empty and will work in the majority (all?) browsers. The question is regarding the RFC confusion and if it is actually valid, defined behaviour that will remain for as long as the RFC is in use.

---

### Post by slavik on 2009-08-22
> **AlexC_ said:**
> Thanks, though I'm aware it *can* be empty and will work in the majority (all?) browsers. The question is regarding the RFC confusion and if it is actually valid, defined behaviour that will remain for as long as the RFC is in use.
I think you answered your own question in your original post, so in a word: yes.

---

### Post by wmcbrine on 2009-08-22
Ask the [validator]("http://validator.w3.org/").

---

### Post by v8YKxgHe on 2009-08-23
> Ask the validator. 
The W3C HTML validator only checks if the markup is valid HTML, it wouldn't check against RFCs to see if things like this are correct.

> I think you answered your own question in your original post, so in a word: yes. 

Appears to be that way :)

---

