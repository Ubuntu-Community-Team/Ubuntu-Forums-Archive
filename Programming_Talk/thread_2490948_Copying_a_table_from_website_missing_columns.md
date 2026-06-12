---
title: "Copying a table from website: missing columns"
date: 2023-09-21
forum: Programming Talk
---

### Post by alfredino on 2023-09-21
Hello,
there is a website from which I would like to copy and paste a table. However, I can only copy some columns as the others cannot be selected. I have also tried python and selenium, but the result is the same.
Is there any way to get all the data from the various columns? Or can they be blocked on the server side?
Thank you


P.S. this usually works without any problem


```

table = driver.find_element(By.CSS_SELECTOR, 'table')


df = pd.read_html(table.get_attribute('outerHTML'))[0]

```

---

### Post by TheFu on 2023-09-21
pandoc?
htmltotext?

If there is javascript involved, lots of negative things are possible.

---

