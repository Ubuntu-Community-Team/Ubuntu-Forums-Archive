---
title: "Custom Action command line help - extracting archives"
date: 2017-06-26
forum: New to Ubuntu
---

### Post by tracyspda on 2017-06-26
Greetings,

I am aware that similar questions have been asked in the past, and believe me I have spent a few hours searching for an answer to this specific question. I have found some resources, but apparently I am either missing the answer or my search terminology is flawed.

First, I am working in Ubuntu 17.04. I am using Thunar as a file manager, although the same situation obtains in Nautilus.

I have a number of archive files (various formats - some zip, some rar, some others) that I am attempting to extract. I wish to extract these archives en masse (by selecting all of the archives, then right-clicking and choosing Extract Here (or some variant thereof) and having them extracted each to their own folders within the current folder).

For archives which contain more than one file, using Extract Here works as expected - a folder is created in the current folder, and the archive is extracted into that folder (mirroring any folder structure that exists in the archive). All well and good.

However, for archives that contain a single file, these files are extracted into the current working folder, rather than having their own sub-folders created. This is where I am having problems - I cannot seem to find any way to have these extracted into separate sub-folders using Extract Here. (I realize that I could open a terminal session and use various (sometimes arcane) commands to extract these archives in the manner that I would like, but this is a fairly common operation for me, and it would be easiest if the Extract Here option on the context menu worked consistently regardless of the contents of the archive.)

I am, therefore, attempting to create a custom action for Thunar (or Nautilus, or both) that will correctly handle this situation, without having to create one custom action per file type. However, I am not able to find a correct command to accomplish this. I did read the man page on file-roller (which is the archive manager used by default from Thunar and Nautilus), and have experimented with various options, but have been unsuccessful when dealing with archives that contain a single file.

Does anyone have a suggestion other than

```
file-roller --force --extract-here *file*
```

(which seems to be the option used for the default operation of the Extract Here context menu command)?

Any pointers - whether to man pages, previously posted materials, FAQs or other help resources - would be appreciated.

Again, as a summary, I am trying to cause archives containing single files to be treated the same as archives containing multiple files / internal folder structures when using Extract Here - whether by changing options or creating a new context menu item.

Thank you in advance for any suggestions.

Tracy

---

