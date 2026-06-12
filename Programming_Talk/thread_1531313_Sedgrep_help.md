---
title: "Sed/grep help"
date: 2010-07-14
forum: Programming Talk
---

### Post by PurposeOfReason on 2010-07-14
I'm using sed/grep to find the current file location playing in mpd so that I can display the cover art that is in the same folder. Using (yes it's quick, dirty, and ugly):
```

"`mpc --format %file% | head -n 1 | sed -e 's/ /\\\ /g' | sed -e 's/\[/\\\[/g'`"

```
amongst other things I can get this:
```

/media/music/0New/School\ of\ Emotional\ Engineering/\[2004]\ School\ of\ Enotional\ Engineering/03\ Falling\ for\ Sylvia.flac

```

Which is a valid location. What I'm trying to do is now trim it to just
```
/media/music/0New/School\ of\ Emotional\ Engineering/\[2004]\ School\ of\ Enotional\ Engineering/
```
so that I can throw a *.jpg|png onto the end of it.

---

### Post by Bachstelze on 2010-07-14
You want dirname:

```
firas@tsukino ~ % dirname "/media/music/0New/School\ of\ Emotional\ Engineering/\[2004]\ School\ of\ Enotional\ Engineering/03\ Falling\ for\ Sylvia.flac"
/media/music/0New/School\ of\ Emotional\ Engineering/\[2004]\ School\ of\ Enotional\ Engineering
```

---

### Post by geirha on 2010-07-15
I'm assuming that mpc command you have there outputs the file playing, and only that? If so, try:
```
# Bash
read -r -d '' < <(mpc --format %file%)

echo "File playing: $REPLY"

dir=${REPLY%/*}
echo "Looking for image files in $dir:"

# Notice the quotes around $dir. If you omit them, it breaks.
for f in "$dir"/*.{jpg,png}; do
  [[ -f $f ]] || continue
  echo "Opening '$f' in the default viewer"
  xdg-open "$f"
done

# Or with the shell options extglob and nullglob:
shopt -s extglob nullglob
for f in "$dir"/*.+(jpg|png); do
  echo "Opening '$f' in the default viewer"
  xdg-open "$f"
done

```

Your seds were adding literal backslashes to the file-path, which is wrong. Just remember to quote the expansion of the variable when you use it; "$file", not $file.

[http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words)
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)
[http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)

EDIT: erhm, hang on. The head -n 1 confused me a bit. Instead of the read, just do
```
file=$(mpc --format %file%)
# and then
dir=${file%/*}

```
Or if it outputs more than that one file, and you want the first one separated by newline:
```
read -r < <(mpc --format %file%)
```

---

