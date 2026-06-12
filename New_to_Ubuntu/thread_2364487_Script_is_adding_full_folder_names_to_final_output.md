---
title: "Script is adding full folder names to final output"
date: 2017-06-23
forum: New to Ubuntu
---

### Post by crenor on 2017-06-23
I am using [COLOR=#000000][FONT=Arial]mkvpropedit to edit the video file title metadata (mkv files)[/FONT][/COLOR]

I have this
[COLOR=#000000][FONT=Arial]for f in *.mkv; do mkvpropedit "$f" --edit info --set "title=${f%.mkv}"; done
[/FONT][/COLOR]
that works on only the folder I am using - so no good


I have this
[COLOR=#000000][FONT=Arial]for f in **/*.mkv; do mkvpropedit "$f" --edit info --set "title=${f%.mkv}"; done
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]as well as[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]for f in `find /workingfolder/ -name *.mkv`; do mkvpropedit "$f" --edit info --set "title=${f%.mkv}"; done[/FONT][/COLOR]

BUT it adds the full folder path to the title

SO, how do I set it to run on a folder, and all subfolders, with the final data not showing the full path / any folders.

---

### Post by sisco311 on 2017-06-23
You can use parameter expansion:

```

shopt -s extglob
for file in **/*.mkv
do
    name=${file##*/}
    name=${name%.mkv}
    mkvpropedit "$file" --edit info --set "title=${name}"
done

```

---

