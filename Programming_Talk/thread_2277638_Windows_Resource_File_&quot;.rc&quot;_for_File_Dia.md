---
title: "Windows Resource File &quot;.rc&quot; for File Dialog"
date: 2015-05-10
forum: Programming Talk
---

### Post by fugu2 on 2015-05-10
I would like to add a "simple" file dialog button to my simple c program, but Em having trouble finding any examples of how to do this. What I would like is to have one button on my main dialog window that , when pressed, opens a file select dialog window. Does anyone know if there is a sample demo floating around anywhere?

---

### Post by fugu2 on 2015-05-11
I kind of answered my own problem, sort of. I found this snippet:
```
	OPENFILENAME ofn;
	char szFile[MAX_PATH];

	ZeroMemory(&ofn, sizeof(ofn));
	ofn.lStructSize = sizeof(ofn);
	ofn.lpstrFile = szFile;
	ofn.lpstrFile[0] = '\0';
	ofn.hwndOwner = hwnd;
	ofn.nMaxFile = sizeof(szFile);
	ofn.lpstrFilter = TEXT("All files(*.*)\0*.*\0");
	ofn.nFilterIndex = 1;
	ofn.lpstrInitialDir = NULL;
	ofn.lpstrFileTitle = NULL;
	ofn.Flags = OFN_PATHMUSTEXIST | OFN_FILEMUSTEXIST;

	if(!GetOpenFileName(&ofn))
		return 1;
	else
		return 0;

```which when executed, opens that WINAPI style file dialog box.

---

