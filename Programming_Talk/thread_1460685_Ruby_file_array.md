---
title: "Ruby file array"
date: 2010-04-23
forum: Programming Talk
---

### Post by Minky2k on 2010-04-23
Hi! How can I in Ruby read a string from a file into an array and only read and save in the array until I get a certain marker such as ":" and stop reading? 

Any help would be much appreciated =)

For example:
```
10.199.198.10:111  test/testing/testing  (EST-08532522)
10.199.198.12:111  test/testing/testing  (EST-08532522)
10.199.198.13:111  test/testing/testing  (EST-08532522)

```

Should only read the following:
```
10.199.198.10
10.199.198.12
10.199.198.13

```

---

### Post by dv3500ea on 2010-04-25
```

def file_to_array path
    (File.new path).read().gsub(/:.*\n/, "\n").split(/\n/)
end

file_to_array 'filepath'

```

---

