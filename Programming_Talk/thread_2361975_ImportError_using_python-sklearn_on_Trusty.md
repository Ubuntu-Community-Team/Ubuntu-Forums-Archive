---
title: "ImportError using python-sklearn on Trusty"
date: 2017-05-22
forum: Programming Talk
---

### Post by Rocket2DMn on 2017-05-22
Using Ubuntu 14.04 for this, I'm getting a python ImportError trying to use scikit-learn (python-sklearn 0.14).  I'm afraid my python experience is limited and I haven't been able to resolve this.  I have python-joblib and python-parallel installed, but get an error with a transitive import.

```

Traceback (most recent call last):
  File "pcm_ee_classifier_dvfs.py", line 12, in <module>
    from sklearn import decomposition
  File "/usr/lib/python2.7/dist-packages/sklearn/decomposition/__init__.py", line 9, in <module>
    from .kernel_pca import KernelPCA
  File "/usr/lib/python2.7/dist-packages/sklearn/decomposition/kernel_pca.py", line 12, in <module>
    from ..metrics.pairwise import pairwise_kernels
  File "/usr/lib/python2.7/dist-packages/sklearn/metrics/__init__.py", line 37, in <module>
    from .scorer import make_scorer, SCORERS
  File "/usr/lib/python2.7/dist-packages/sklearn/metrics/scorer.py", line 29, in <module>
    from .cluster import adjusted_rand_score
  File "/usr/lib/python2.7/dist-packages/sklearn/metrics/cluster/__init__.py", line 19, in <module>
    from .unsupervised import silhouette_samples
  File "/usr/lib/python2.7/dist-packages/sklearn/metrics/cluster/unsupervised.py", line 10, in <module>
    from ..pairwise import pairwise_distances
  File "/usr/lib/python2.7/dist-packages/sklearn/metrics/pairwise.py", line 50, in <module>
    from ..externals.joblib import parallel
ImportError: cannot import name parallel

```

Any help is appreciated.  If I need to download a newer version of sklearn and install to a separate directory, I can give it a go, but I've never done that before with python, so recommendations on how to do that properly are also appreciated.  Thanks.

Edit: FYI, I don't have this problem on my laptop running Ubuntu 16.04 (Xenial) with python-sklearn 0.17.

---

### Post by Rocket2DMn on 2017-05-23
I resolved this by installing a newer version of scikit-learn using pip:
```
sudo pip install -U scikit-learn
```

---

