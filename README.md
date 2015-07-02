syncdb
=======
This tools enables to transfer data by query between differnt database servers.
Currently it supports to connect to PostgreSQL, Oracle Database.

Quick Introduction
---
With syncdb, users can synchonize data from one database server to other database server:

Setting which data to be replicate by SQL.
````
$ syncdb attach --master pg_mdb --server pg_rdb --schema public --table rep_accounts
input query : SELECT aid, bid, abalance FROM "public"."pgbench_accounts"
INFO  - attach incremental refresh mode, subscribe id : 1
````

Then, syncdb can transfer data with full refresh mode or incremental mode.
 ````
 $ syncdb refresh --server pg_rdb --schema public --table rep_accounts --mode auto
INFO  - full refresh (insert:100,000)
````

````
$ syncdb refresh --server pg_rdb --schema public --table rep_accounts --mode auto
INFO  - incremental refresh (insert:0 update:1,000 delete:0)
````

Please take a look to documentation http://ossc-db.github.io/syncdb/index.html.


