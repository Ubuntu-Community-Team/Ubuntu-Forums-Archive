---
title: "zipfile in python"
date: 2010-08-03
forum: Programming Talk
---

### Post by 98174 on 2010-08-03
I make a temp directory inside the current working directory, download images to temp, package them using zipfile, and then copy the zipfile out to another location.  It works file, but the zipfile copies the folder structure of the temp folder, i.e. instead of an archive with 001.jpg, 002.jpg, 003.jpg...I have instead temp/001.jpg, temp/002.jpg, temp/003.jpg

Any way to remedy this?

---

### Post by Bachstelze on 2010-08-03
What's your code?

---

### Post by 98174 on 2010-08-03
```
def compress(mangaChapterPrefix, current_chapter, download_path, current_page, download_format):
	print('Compressing...')
	z = zipfile.ZipFile('mangadl_tmp/' + mangaChapterPrefix + download_format, 'a')
	for page in range(1, current_page + 1):
		z.write('mangadl_tmp/' + mangaChapterPrefix + '_' + str(page).zfill(3) + '.jpg')
	shutil.move('mangadl_tmp/' + mangaChapterPrefix + download_format, download_path)
	cleanTmp()
```

The images are stored in mangadl_tmp.  My intention is to create the zip archive inside the tmp folder as well, then move it out to download_path.

---

### Post by Bachstelze on 2010-08-03
We're not supposed to help with illegal stuff, but have a look at the [font=monospace]arcname[/font] argument to [font=monospace]write()[/font].

---

### Post by Jacobian on 2010-08-03
Here is something that might work:

You could change to the "mangadl_tmp" directory before issuing the zip command:
[http://docs.python.org/library/os.html](http://docs.python.org/library/os.html)

---

### Post by 98174 on 2010-08-03
Changing [font=monospace]arcname[/font] fixed it for me.  I assumed the default behavior of [font=monospace]write[/font] was to grab the filename and not the full path passed to it, but this was not the case.

```
z.write('mangadl_tmp/' + mangaChapterPrefix + '_' + str(page).zfill(3) + '.jpg', mangaChapterPrefix + '_' + str(page).zfill(3) + '.jpg')

```

---

### Post by Martin Witte on 2010-08-03
to clean up your code and to make it more portable across platforms  I would introduce a variable for the filename, and I would use the join method in the os.path library, you get then
```
filename = mangaChapterPrefix + '_' + str(page).zfill(3) + '.jpg'
z.write((os.path.join('mangadl_tmp', filename), filename))

```

---

### Post by 98174 on 2010-08-03
Done - thanks for pointing this out.  I'd actually been wondering about this for a long time.

---

