---
title: "tinyman-py-sdk: python interpreter can't find module"
date: 2021-12-28
forum: Programming Talk
---

### Post by drjdmartin on 2021-12-28
Hi,

I'm trying to get the tinyman-py-sdk to work under Ubuntu 20.04.

I've installed and switched to a virtual env to install as follows:

```

python3 -m venv crypto
source crypto/bin/activate
pip install wheel
pip install git+https://github.com/tinymanorg/tinyman-py-sdk.git

```

I'm then trying to run the following code

```

#!/usr/bin/env python3
# -*- coding: utf-8 -*-

from tinyman.v1.client import TinymanTestnetClient

client = TinymanTestnetClient()

# Fetch our two assets of interest
TINYUSDC = client.fetch_asset(21582668)
ALGO = client.fetch_asset(0)

# Fetch the pool we will work with
pool = client.fetch_pool(TINYUSDC, ALGO)

# Get a quote for a swap of 1 ALGO to TINYUSDC with 1% slippage tolerance
quote = pool.fetch_fixed_input_swap_quote(ALGO(1_000_000), slippage=0.01)
print(quote)
print(f'TINYUSDC per ALGO: {quote.price}')
print(f'TINYUSDC per ALGO (worst case): {quote.price_with_slippage}')

```

Saving the file as tinyman.py and trying to run in the terminal using the command "python3 tinyman.py" I get the following error

```

Traceback (most recent call last):
  File "tinyman.py", line 4, in <module>
    from tinyman.v1.client import TinymanTestnetClient
  File "/home/james/Python/tinyman.py", line 4, in <module>
    from tinyman.v1.client import TinymanTestnetClient
ModuleNotFoundError: No module named 'tinyman.v1'; 'tinyman' is not a package

```

I can't really understand why the interpreter can't find the module from a virtual env. Any ideas?

Thanks,

James

---

### Post by norobro on 2021-12-28
> **drjdmartin said:**
> Hi,
Saving the file as tinyman.py and trying to run in the terminal using the command "python3 tinyman.py" I get the following error

Try changing the name of this file.

---

### Post by drjdmartin on 2021-12-29
Thanks v much - yes that did the trick

Lesson learned - call your file something different to the module...

---

