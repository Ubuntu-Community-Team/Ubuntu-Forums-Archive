---
title: "[Gio] Mount related question"
date: 2010-08-24
forum: Programming Talk
---

### Post by kahumba on 2010-08-24
Hi,
there seems to be no Gio (gtkmm) examples related to this,
any ideas how to mount a volume and then figure out where it has been mounted?

---

### Post by jpaugh64 on 2010-08-24
0

---

### Post by kahumba on 2010-08-24
Thanks, unfortunately I have to do it programmatically (in C++ using Gio which is part of Gtkmm). btw I played with Gio and it seems either broken or unfinished.

---

### Post by kahumba on 2010-08-24
Problem solved 50%.
Though
1) Can't use source_object cause don't know how to cast it to make it usable.
2) The volume's get_mount() and get_uuid() always return null and an empty string respectively. No idea why.

In case anyone needs it as a reference:
```

//class PlacesItem

//method called when mounting
void PlacesItem::onResult(Glib::RefPtr<Gio::AsyncResult>& result) {

    Glib::RefPtr<Glib::Object> source_object = result->get_source_object(); //no way to cast it
    bool success = volume->mount_finish(result);
    if (!success) {
        std::cout << "failed to mount the volume" << std::endl;
        return;
    }
    std::cout << "mounted successfully, though no idea how to use source_object" << std::endl;
}

//this method is an event handler to mount a volume
//which is a Glib::RefPtr<Gio::Volume> created earlier

void PlacesItem::on_activate() {
    if (!volume->can_mount()) {
        std::cout << "can't mount" << volume->get_name() << std::endl;
        return;
    }
    volume->mount(Gio::MountOperation::create(), sigc::mem_fun(*this, &PlacesItem::onResult));
}


```

---

### Post by SledgeHammer_999 on 2010-08-24
Gio::AsyncResult::get_source_object() is deprecated according to the [docs](http://library.gnome.org/devel/glibmm/unstable/classGio_1_1AsyncResult.html). Use Gio::AsyncResult::get_source_object_base instead.

I think to use **source_object** as a Gio::Volume you need to up-cast it using **[Glib::RefPtr< T_CppObject >::cast_static](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1RefPtr.html#a548fd6f5629a269e6ac0fd3db9c4fe6b)**. Something like this:

[php]Glib::RefPtr<Gio::Volume> volume_ptr = Glib::RefPtr<Gio::Volume>::cast_static(source_object);[/php]

If this works then the get_name()/get_uuid() should succeed in this step.

NOTE: I have no experience with this part of Gio. I just tried to see if I can help you by reading the docs.

---

### Post by kahumba on 2010-08-24
Thanks, that works, I only had to replace "static" with "dynamic".
So while I can cast now I don't know what object that is, it doesn't seem to be a Volume cause I get an error after I call any method on that Volume.

So I tried figuring out what type the source_object actually is:
std::cout << "object name: " << typeid(source_object).name() << std::endl;
and it yields:
N4Glib6RefPtrINS_6ObjectEEE

So still no idea. The docs don't mention this either.

---

### Post by kahumba on 2010-08-24
Well I also used the new method result->get_source_object_base() and it works!
It's indeed a Volume, get_name() works, but get_mount() still returns null and get_uuid() is still empty, it might be a bug in gio.

---

### Post by SledgeHammer_999 on 2010-08-24
Also try again using "static" instead of "dynamic", in order to keep with the convention. In raw C++ pointers the dynamic_cast<> works to cast pointers from the derived class to the base class. static_cast<> works the other way around (among other things) link->[http://www.cplusplus.com/doc/tutorial/typecasting/](http://www.cplusplus.com/doc/tutorial/typecasting/)

EDIT: I see that the Glib::RefPtr docs say that the dynamic cast is able to be performed for base-to-derived conversions too. :s 

I suggest that you sign up in the gtkmm mailing list and ask questions about Gio there or even the gtk mailing list if you don't get any answer on the gtkmm's.

---

### Post by kahumba on 2010-08-25
Thanks a lot.

---

