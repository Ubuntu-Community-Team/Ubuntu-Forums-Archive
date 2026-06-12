---
title: "Document Template - Creating a quick .odt file inside a folder"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Cornova on 2008-07-31
When you right-click inside a folder, lets say the 'Home Folder', there is an option called "Create Document." Under this option there is an "Empty File" option, and a faded option block with the phrase "No templates installed."

Often I am inside folders and need to place a general 'notes' document in the folder that is related to the topic. I use the OpenOffice.org word processor for this and it's a pain to have to open the application and then look for the folder where I want to save it.

Is there a way that I can add this under the "Create Document" section? the Empty File option allows me to put in .odt as the file extension, but the format isn't the same as the default one when you simply open up the word processor.

---

### Post by iaculallad on 2008-07-31
On your terminal, Check if the "Templates" folder exist in your HOME directory.

```

ls ~
```

If "Templates" directory does not exist, create it:

```
mkdir ~/Templates
```

Then, open your OpenOffice Word Processor and save a blank file named "OppenOffice.odt" on the ~/Templates directory.
Whenever you right click and select "Create Document", you could see the OpenOffice Template file w/c you had saved earlier on the Templates directory.

---

### Post by Cornova on 2008-07-31
Works perfect, thank you!

---

