---
title: "Need help with editing filezilla source code"
date: 2008-08-02
forum: Programming Talk
---

### Post by nix4me on 2008-08-02
Hi,

I am trying to remove a "feature" of filezilla that is causing me problems.  Basically, filezilla is giving me an error about certificate mismatches and i want to remove this security check.  I asked on the filezilla forum and they said to hack the source and recompile.  I found the area of concern in the source but i don't know how to remove.  Here is the relevant area in the source:


```
}

	if (m_implicitTrustedCert.data)
	{
		if (m_implicitTrustedCert.size != cert_list[0].size ||
			memcmp(m_implicitTrustedCert.data, cert_list[0].data, cert_list[0].size))
		{
			m_pOwner->LogMessage(::Error, _("Primary connection and data connection certificates don't match."));
			Failure(0, ECONNABORTED);
			return FZ_REPLY_ERROR;
		}

		TrustCurrentCert(true);

		if (m_tlsState != conn)
			return FZ_REPLY_ERROR;
		return FZ_REPLY_OK;
	}
```

Any ideas on how I keep filezilla from making the check and then giving me the "Primary connection and data connection certificates don't match." error?

Any help would be appreciated,
nix4me

---

