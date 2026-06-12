---
title: "Evolution VCard Import From Python"
date: 2009-04-07
forum: Programming Talk
---

### Post by longfeltwant on 2009-04-07
I am trying to write a script to sync my contacts from Evolution (on my Ubuntu netbook) to Soocial (which is a contact-management website/service).

To achieve this I got the py-soocial package (Python bindings to the Soocial API) and evolution-python (Python bindings to the Evolution contact API). I am able to get contacts out of Soocial and Evolution as either objects or, by using methods in those packages, as VCards (text).

My limitation, however, is that apparently Evolution does not have a command-line method for importing VCard information. It can export VCards from the command line, and it can import VCards from the GUI.

I could write code to translate the VCard text into objects (or, actually, from soocial-type objects to evolution-type objects), but it would be better to use the VCard standard to transfer the data.

Can anybody point me to a way to push VCard data into evolution from a Python script? I'm new to Linux programming so this might be a silly question.

---

### Post by longfeltwant on 2009-04-07
I figured out that you can initialize an EContact using the text of a VCard:

book = ebook.open_addressbook("default")
evo_contact = ebook.EContact(vcard_string)
book.add_contact(evo_contact)

That's great, and I have successfully put contacts into Evolution. However, I am having another problem with deciding whether or not a contact is already in Evolution. I know there is a search interface, but I don't know how to use it because for the life of me I can't find the API doc anywhere online.

---

