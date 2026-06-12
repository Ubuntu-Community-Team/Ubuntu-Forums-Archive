---
title: "Gambas TextArea/TextEdit Coloring"
date: 2008-09-07
forum: Programming Talk
---

### Post by briansykes on 2008-09-07
Hey everyone i'm wondering how to change the color of an individual line of text in a textarea or text edit i tried this and it just sets the forecolor to the color.

```
PUBLIC SUB addToLog(Text AS String, OPTIONAL TextColor AS Integer)
  DIM strPos AS Integer, endPos AS Integer
  txtlog.Insert(Text & "\n")
  strPos = InStr(txtLog.Text, Text)
  endPos = strPos + Len(Text)
  txtLog.Select(strPos, endPos)
  txtLog.ForeColor = TextColor
  txtLog.Unselect
END
```

I don't know if its possible but i'm trying to make a chat and being able to change the colors in a line of text in the chat log is needed.

---

