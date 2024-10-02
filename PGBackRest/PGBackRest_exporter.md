Backup Failure Alert

```
- alert: PGBackRestBackupFailure
  expr: pgbackrest_backup_last_ok == 0
  for: 5m
  labels:
    severity: critical
  annotations:
    summary: "PGBackRest backup failure"
    description: "The last PGBackRest backup failed. Please check the backup logs for more details."
```

Backup Duration Alert
```
- alert: PGBackRestBackupDurationHigh
  expr: pgbackrest_backup_duration_seconds > 3600
  for: 5m
  labels:
    severity: warning
  annotations:
    summary: "PGBackRest backup duration high"
    description: "The last PGBackRest backup took longer than expected. Please investigate the cause."
```
Backup Size Alert
```
- alert: PGBackRestBackupSizeHigh
  expr: pgbackrest_backup_size_bytes > 1e+10
  for: 5m
  labels:
    severity: warning
  annotations:
    summary: "PGBackRest backup size high"
    description: "The size of the last PGBackRest backup is unusually large. Please investigate the cause."
```
Backup Age Alert
```
- alert: PGBackRestBackupAgeHigh
  expr: time() - pgbackrest_backup_last_timestamp > 86400
  for: 5m
  labels:
    severity: warning
  annotations:
    summary: "PGBackRest backup age high"
    description: "The last PGBackRest backup is older than 24 hours. Please ensure backups are running as scheduled."
```
Backup Retention Alert
```
- alert: PGBackRestBackupRetentionLow
  expr: pgbackrest_backup_retention_days < 7
  for: 5m
  labels:
    severity: warning
  annotations:
    summary: "PGBackRest backup retention low"
    description: "The backup retention period for PGBackRest is less than 7 days. Please review the retention policy."
```
Backup Compression Ratio Alert
```
- alert: PGBackRestBackupCompressionRatioLow
  expr: pgbackrest_backup_compression_ratio < 0.5
  for: 5m
  labels:
    severity: warning
  annotations:
    summary: "PGBackRest backup compression ratio low"
    description: "The compression ratio of the last PGBackRest backup is unusually low. Please investigate the cause."
```
Backup Encryption Alert
```
- alert: PGBackRestBackupEncryptionDisabled
  expr: pgbackrest_backup_encryption == 0
  for: 5m
  labels:
    severity: critical
  annotations:
    summary: "PGBackRest backup encryption disabled"
    description: "Backup encryption is disabled for PGBackRest. Please enable encryption to secure your backups."
```
Backup Repository Space Alert
```
- alert: PGBackRestBackupRepositorySpaceLow
  expr: pgbackrest_backup_repository_space_bytes < 1e+10
  for: 5m
  labels:
    severity: warning
  annotations:
    summary: "PGBackRest backup repository space low"
    description: "The available space in the PGBackRest backup repository is low. Please free up space or increase the repository size."
```