---
title: "MonoDevelop can't import VS2013/2015 solutions"
date: 2015-06-27
forum: Programming Talk
---

### Post by James_Ko on 2015-06-27
I'm opening a .sln file that I transferred from Visual Studio 2013 into MonoDevelop. When I attempt this, however, it gives me the following error(s):


```
1. Project 'foo' has a different ToolsVersion than the containing solution.
2. Error while trying to load the project '/path/to/foo.csproj': Unknown ToolsVersion '12.0'
3. [repeat 2 for every project in the solution]
```

When I tried doing this for a VS2015 file, it game me the same errors, except this time ToolsVersion was 14.0.


My MonoDevelop version is v4.0.12; is there a workaround for this?

---

