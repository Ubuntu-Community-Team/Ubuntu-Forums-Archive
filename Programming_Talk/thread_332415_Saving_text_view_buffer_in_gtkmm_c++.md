---
title: "Saving text_view buffer in gtkmm c++"
date: 2007-01-06
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-06
Can anyone show me how to make a fstream like thing that saves the buffer into a file?
Also how to make a save file dialog?

---

### Post by cabalas on 2007-01-06
the save dialog works much the same way as the open one does, it's still a file chooser dialog save that the file chooser action is Gtk::FILE_CHOOSER_ACTION_SAVE, to write the text out to the file once it was open all I'd do is (assuming file is the filestream and mText is the Gtk::TextView):

```

  file << mText.get_buffer()->get_text();

```

Hope that helps.

---

