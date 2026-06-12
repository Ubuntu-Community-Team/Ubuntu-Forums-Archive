---
title: "joblib passing parameter error AttributeError: 'module' object has no attribute"
date: 2018-04-14
forum: Programming Talk
---

### Post by zerop2 on 2018-04-14
[FONT=Arial]Process PoolWorker-1: [/FONT]
[FONT=Arial]Traceback (most recent call last): [/FONT]
[FONT=Arial]  File "C:\Python27\lib\[/FONT][FONT=Arial]multiprocessing\process.py", line 258, in _bootstrap [/FONT]
[FONT=Arial]    self.run() [/FONT]
[FONT=Arial]  File "C:\Python27\lib\[/FONT][FONT=Arial]multiprocessing\process.py", line 114, in run [/FONT]
[FONT=Arial]    self._target(*self._args, **self._kwargs) [/FONT]
[FONT=Arial]  File "C:\Python27\lib\[/FONT][FONT=Arial]multiprocessing\pool.py", line 102, in worker [/FONT]
[FONT=Arial]    task = get() [/FONT]
[FONT=Arial]  File "C:\Python27\lib\site-[/FONT][FONT=Arial]packages\joblib\pool.py", line 362, in get [/FONT]
[FONT=Arial]    return recv() [/FONT]
[FONT=Arial]AttributeError: 'module' object has no attribute 'easysearch' [/FONT]


[FONT=Arial]how to solve this bug? [/FONT]

[FONT=Arial]import re [/FONT]
[FONT=Arial]import string [/FONT]
[FONT=Arial]from itertools import permutations [/FONT]
[FONT=Arial]from itertools import combinations [/FONT]
[FONT=Arial]from joblib import Parallel, delayed [/FONT]
[FONT=Arial]import multiprocessing [/FONT]
[FONT=Arial]from multiprocessing import Process, freeze_support [/FONT]

[FONT=Arial]all_normal_characters = string.ascii_letters + string.digits [/FONT]
[FONT=Arial]def is_special(character): [/FONT]
[FONT=Arial]    return character not in all_normal_characters [/FONT]

[FONT=Arial]def easysearch(content): [/FONT]
[FONT=Arial]    if len(str(content[0]).strip()) == 0 or len(str(content[1]).strip()) == 0: [/FONT]
[FONT=Arial]        return "" [/FONT]
[FONT=Arial]    row1 = content[0] [/FONT]
[FONT=Arial]    keywords = content[1] [/FONT]
[FONT=Arial]....... [/FONT]

[FONT=Arial]num_cores = multiprocessing.cpu_count() [/FONT]

[FONT=Arial]def segmentsearch(content, findwhat, lensize): [/FONT]
[FONT=Arial]    chunks, chunk_size = len(content), lensize [/FONT]
[FONT=Arial]    result = Parallel(n_jobs=num_cores)([/FONT][FONT=Arial]delayed(easysearch)([content[[/FONT][FONT=Arial]j:j+chunk_size], findwhat]) for j in range(0, chunks, chunk_size)) [/FONT]
[FONT=Arial]    print(result) [/FONT]
[FONT=Arial]    return result [/FONT]

[FONT=Arial]def main(): [/FONT]
[FONT=Arial]    result = segmentsearch("search key    $  @   $  wrds today", "key words", 77) [/FONT]
[FONT=Arial]    print(result) [/FONT]


[FONT=Arial]if __name__=="__main__": [/FONT]
[FONT=Arial]    freeze_support() [/FONT]
[FONT=Arial]    main() [/FONT]

---

