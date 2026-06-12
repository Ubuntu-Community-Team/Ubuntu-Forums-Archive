---
title: "Rails: updating a client browser when an event happens on the server"
date: 2007-08-15
forum: Programming Talk
---

### Post by saracen on 2007-08-15
I'm looking for a framework that will allow me to update client browsers when events happen on the server.  So the use case would be for example a chat application - when a message comes in from another user onto the server it sends an update down to the client.  Google does stuff like this with Gtalk on the Gmail webpage.  Another example would be a virtual meeting service - when someone joins the meeting the other participants of the meeting would get a UI update on their browsers viewing the webpage.

What is the best framework out there that integrates well with Ruby on Rails?  Scalability is critical here as well as it seems like the connections would have to be long-lived, or re-opened after a chunk of data is pushed down to the client.

Any pointers on this would be helpful.  Is there a preferred rails way to do this?

---

### Post by Modred on 2007-08-15
You should investigate the Prototype javascript library; it's bundled with Rails and Rails comes with helper functions to make writing the calls less error prone.  You can set up a variety of update schemes, such as when a form or form field changes, when a button or link is clicked, or after a set interval of time.

The **periodically_call_remote** helper function would probably give you functionality like what you're looking for.  It isn't exactly responding to a server event, but allows you to check for changes on the server at regular intervals.

The one caveat here is that AJAX can be a bit slow.  But a good deal of Gmail and friends are built around AJAX, so that should give you a decent idea of how performance could go.  (Of course, I imagine Google uses a custom built AJAX framework, which may have better performance than Prototype.)

---

