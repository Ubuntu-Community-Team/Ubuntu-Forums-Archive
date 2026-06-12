---
title: "[SOLVED] completed file."
date: 2008-09-12
forum: Programming Talk
---

### Post by StOoZ on 2008-09-12
how can I check whether a file , is written completely by the OS?
I mean , I have this code :
>         curl_easy_setopt(curl, CURLOPT_WRITEDATA, pf);
        curl_easy_perform(curl);
......
        std::fstream html_f( html_page_namer.c_str() , std::ios_base::in );
        html_f.seekg(0 , std::ios_base::end);
        size_t file_size = html_f.tellg();


the function 'curl_easy_perform' downloads a page , when I check its size , I dont get the full size , but when I rename it , and then check its size , I get the real size.
I think that it happens coz when I check its size with the original name , the system is yet to complete that file , and thats why Im getting the wrong size , right?

so , how to solve this issue?

---

### Post by Zugzwang on 2008-09-12
> **StOoZ said:**
> so , how to solve this issue?

I would say by waiting curl to complete its task (if using multi-threading) and closing the file after writing before opening it a second time.

---

### Post by StOoZ on 2008-09-12
thanks a lot , your suggestion popped something else in my mind that solved the issue , used fflush(pf);

---

