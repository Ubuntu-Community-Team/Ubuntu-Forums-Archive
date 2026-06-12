---
title: "How to Realize this Replace Purpose"
date: 2009-06-09
forum: Programming Talk
---

### Post by huangyingw on 2009-06-09
Hello, I would like a regulor expression to realize my replace purpose.
origin strings:
```

\\STBReleases\releases\bj2_brcm_1.6_Builds\bj2_brcm_1.6_1119\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat
\\STBReleases\releases\new_branch_Builds\new_branch_1119\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat
\\STBReleases\releases\abc-brahcn_Builds\abc-brahcn_1119\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat

```
The target string I desire. 
Take the first line  for example:
```

\\STBReleases\releases\bj2_brcm_1.6_Builds\bj2_brcm_1.6_1119\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat

```
My intention is to match out the branch name "bj2_brcm_1.6" before "Builds".And then, I would use the "bj2_brcm_1.6" to find out the number "1119" behind it. And finally replace it with my expecting "myNum". That's all my process.
The final is the target outputs I would like, you see, the branch names migh differ.
```

\\STBReleases\releases\bj2_brcm_1.6_Builds\bj2_brcm_1.6_myNum\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat
\\STBReleases\releases\new_branch_Builds\new_branch_myNum\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat
\\STBReleases\releases\abc-brahcn_Builds\abc-brahcn_myNum\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat

```

---

### Post by ghostdog74 on 2009-06-09
what have you tried?

```

awk 'BEGIN{ FS="\\"}
{
 o=$6
 gsub(/_[0-9]*$/,"",o)
 $6=o "_" "mynum"
}1' OFS="\\" file

```

---

### Post by huangyingw on 2009-06-09
Yes. Tring to re do my efforts:(
I have many half way tries, I have difficulty at combine them together:(
this string
```

((?!Builds).)+

```
return me with the following, I don't know how to cut off the prefix string "\\STBReleases\releases\". I want to match out the "bj2_brcm_1.6_" first, then use the (\1) to reuse it to match out the 1119 in tv2_brcm_1.6_1119
```

\\STBReleases\releases\bj2_brcm_1.6_

```

---

### Post by huangyingw on 2009-06-09
> **ghostdog74 said:**
> what have you tried?

```

awk 'BEGIN{ FS="\\"}
{
 o=$6
 gsub(/_[0-9]*$/,"",o)
 $6=o "_" "mynum"
}1' OFS="\\" file

```
Thank for your answer, while I know little about awk. Could this be realized purely in regular expression, so I could use it every where?
My weak is even I know how to match out the number 1119, while, I don't know how to replace it purely with regular expression:(

---

