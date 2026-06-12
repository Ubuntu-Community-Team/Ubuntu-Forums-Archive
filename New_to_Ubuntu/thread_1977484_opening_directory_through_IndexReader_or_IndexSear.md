---
title: "opening directory through IndexReader or IndexSearcher?in lucene"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by rrsk on 2012-05-10
what is the difference between these two codes? based on performance oriented and documentation oriented

using directory directly in IndexSearcher

> Analyzer anal = new StandardAnalyzer(Version.LUCENE_30);
QueryParser parser = new QueryParser(Version.LUCENE_30, "", anal);
Query query = parser.parse(queryStr);
Searcher searcher = new IndexSearcher(NIOFSDirectory.open(new File(indexDir)));


using directory in IndexReader then opening searcher using that reader

> Analyzer anal = new StandardAnalyzer(Version.LUCENE_30);
QueryParser parser = new QueryParser(Version.LUCENE_30, "", anal);
Query query = parser.parse(queryStr);
IndexReader ir = IndexReader.open(NIOFSDirectory.open(new File(indexDir)), false);
IndexSearcher searcherNew = new IndexSearcher(ir);


---

