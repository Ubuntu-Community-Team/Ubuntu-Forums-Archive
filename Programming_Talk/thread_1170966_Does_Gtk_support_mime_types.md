---
title: "Does Gtk support mime types?"
date: 2009-05-26
forum: Programming Talk
---

### Post by cl333r on 2009-05-26
Hi,
Is there anything in Gtk where one can pass a file or a file path and get in return it's mime type?
I.e. "/usr/example.html" would return "text/html"..

Google seems quiet about it.

---

### Post by crdlb on 2009-05-26
You can use GIO; here's an example in vala ```

int main (string[] args) {

    if (args.length < 2) {
        printerr ("Error: need at least one argument\n");
        return 1;
    }

    var file = File.new_for_commandline_arg (args[1]);

    try {
        var file_info = file.query_info ("standard::content-type", 0, null);
        print ("content type is: %s\n", file_info.get_content_type ());
    } catch (Error e) {
        printerr ("Error: %s\n", e.message);
        return 1;
    }

    return 0;
}

```

Should compile with ```
valac mimetype.vala --pkg gio-2.0
``` if you want to try it as-is.

---

### Post by cl333r on 2009-05-26
Thanks!
I compiled it, your Vala example works fine. I'm using C++ so I had a look at the api for Gio::File and I think Gio is very powerful, but to leverage its potential a newbie like me needs an equally powerful tutorial.. So far I found plain examples, which is good.

---

### Post by cl333r on 2009-05-27
I suspect Gio uses the [shared mime database]("http://www.freedesktop.org/wiki/Specifications/shared-mime-info-spec") which is designed to also hold the human readable type of the file (like "Html document"), but can't find a way to get it, anyone knows how and if possible from Gio at all?


I tested all "standard" attributes of an SVG image and no human readable one found:
> 
standard::content-type: image/svg+xml
standard::name: preferences-desktop-peripherals.svg
standard::type: 1
standard::size: 27539
standard::allocated-size: 28672
standard::display-name: preferences-desktop-peripherals.svg
standard::edit-name: preferences-desktop-peripherals.svg
standard::copy-name: preferences-desktop-peripherals.svg
standard::icon: GThemedIcon:0x1bdfb20
standard::fast-content-type: image/svg+xml


---

### Post by crdlb on 2009-05-27
Try g_content_type_get_description with the content type you got from the FileInfo.

---

### Post by cl333r on 2009-05-27
Thanks again!

This prints out the result:
```

cout << "Description: " << Gio::content_type_get_description(fileInfo->get_content_type()) << endl;

```

I suspect getting the content type string and the description probably require different resources, if so probably that's why the description is not included into Gio::FileInfo.

---

### Post by crdlb on 2009-05-28
Well, it would be a bit redundant to provide both in the FileInfo if you can get one from the other.

---

