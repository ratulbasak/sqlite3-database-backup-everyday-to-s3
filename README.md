#sqlite3-database-backup-everyday-to-s3#

Configuration includes of AWS credentials, db.sqlite3 file and local backup path...

Daily db backup script is saved which depends on another file named db.sqlite3. This script backups all the files or databases in a single ec2 instance to a specified S3 bucket. The backup script is stored in remote db instance.

First you need to create a *bucket* manually. After putting sqlite_bck.py file in remote machine set the following crojob to autbackup is specific bucket at specific time. To do so first install boto framework in the remote machine.

```
        pip install boto
```

Then add the cronjob for daily databse backup at 1:00 A.M.

```
        crontab -e
```

```
        0 1 * * * python sqlite_bck.py && mail -s "backup of sqlite3-db is successful" user@gmail.com
```

This above cronjob emails to specifed email address if relayhost is configured in the remote machine where cronjob is running.


*NOTE:* You can use this script to create backup of any files you want and upload to aws s3

For this comment line 25, 26 and change file path in line 22 and filename in line 23. Thay's it...
