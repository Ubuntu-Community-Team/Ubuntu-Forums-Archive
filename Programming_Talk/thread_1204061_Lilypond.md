---
title: "Lilypond"
date: 2009-07-04
forum: Programming Talk
---

### Post by matmatmat on 2009-07-04
I have this file:
```

\header {
  title = "Song"
  subtitle = "(tune)"
  composer = "Me"
  tagline = \markup {
  }
}

\version "2.12.1"

%#(set-global-staff-size 16)


up = \drummode {
  \voiceOne
  hh8 <hh sn> hh <hh sn>
  hh8 <hh sn> hh <hh sn>
  hh8 <hh sn> hh <hh sn>
}
down = \drummode {
  \voiceTwo
  bd8 s bd s
  bd8 s bd s
  bd8 s bd s
}

drumContents = {
  <<
    \set DrumStaff.instrumentName = #"Drums"
    \new DrumVoice \up
    \new DrumVoice \down
  >>
}


```

When run it says:
```

GNU LilyPond 2.12.1
Processing `test2.ly'
Parsing...

```
but there is no pdf or ps file

Sorry if this is the wrong place to post this

---

### Post by pacovila on 2009-09-20
You don't obtain a PDF because there is no music on your document.  You define some variables which contain music, but you don't use those variables. From your text it appears that you want \drumcontents to contain the main music, so make it the score using it between curly braces, i.e. just write this at the end:

```
 { \drumContents }
```or remove the drumContents =  part and leave the block as 

```

{
  <<
    \set DrumStaff.instrumentName = #"Drums"
    \new DrumVoice \up
    \new DrumVoice \down
  >>
}
```but this is still not correct because you want to have a DrumStaff with two DrumVoices in it, so prefix that block with \new DrumStaff, remove the curly braces and we'll finally have

```
\new DrumStaff
  <<
    \set DrumStaff.instrumentName = #"Drums"
    \new DrumVoice \up
    \new DrumVoice \down
  >>

```HTH

PD please consider subscribing to the LilyPond mailing list, [http://lists.gnu.org/mailman/listinfo/lilypond-user](http://lists.gnu.org/mailman/listinfo/lilypond-user)

---

