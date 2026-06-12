---
title: "GetInterval()"
date: 2008-05-04
forum: Programming Talk
---

### Post by dodu3784 on 2008-05-04
Hello evrybody,
Have a question about a function I am using with OpenGL (and wxwidgets). 
I have the following function definition:
```

void Vue_OpenGL::OnTimer(wxTimerEvent& event)
{
  position += event.GetInterval() / 15.0;
  while (position > 360.0) position -= 360.0;
  Refresh(false);
}

```
What does exactly GetInterval, does it return an int inialized at 360, is it a default value ?

---

