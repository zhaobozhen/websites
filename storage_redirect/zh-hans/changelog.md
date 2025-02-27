# Changelog

## 2.0.1 (2019-09-27)

- 修复“共享文件夹”规则实际没有生效

## 2.0.0 (2019-09-27)

- 对“共享文件夹”及“同步文件夹”规则进行问题检查（有问题的规则会被删除有问题的部分或禁用），在下个版本会针对这个这个问题提供更加详细的提示及教程
- 修复数个有关“同步文件夹”规则的问题
- 修复独立“修复应用间交互”开关坏掉
- 增强模式 v20.1：修复“修复应用间交互”功能在 OnePlus Android 10（可能还有其他）上的问题
- 大量 UI 改进

## 1.9.1 (2019-09-09)

- 修复“修复应用间交互”可能没有工作的问题
- 增加半透明状态栏及导航栏选项
- 修复数个 UI bug

## 1.9.0 (2019-09-08)

- 增强模式 v20.0：修复使用 [Adoptable Storage](https://source.android.com/devices/storage/adoptable) 时安装在外置存储卡的应用无效的问题
- 增强模式 v20.0：更改“修复应用间交互”功能的实现方法，不再会被“Xposed Taichi”破坏，同时也可能会解决一些其他的问题
- 增强模式 v20.0：“修复应用间交互”可单独为每个应用开关
- 修复备份功能不能还原部分配置的问题
- 在 Android Q 上自动允许 `OP_REQUEST_INSTALL_PACKAGES`（因为其发生变化时会触发系统重新挂载）

## 1.8.3 (2019-08-30)

- 修复一些 UI bug
- 修复“基础模式”下的一个重大问题

## 1.8.2 (2019-08-27)

- 处理特殊系统应用（appId < 10000 或 appId > 19999, appId = uid % 100000）
- 不为特殊系统应用锁定权限
- 其他 bug 修复和 UI 改进

## 1.8.1 (2019-08-26)

- 改进选择“可访问文件夹”流程
- 可直接为“可访问文件夹模板”选择使用的应用
- 修复在 Android Q 上启动服务时对已启动的应用的重定向会失效问题
- 修复长时间停留在主界面 CPU 占用会越来越高问题
- 修复使用 API（暂未公开）的应用崩溃的问题
- 其他 bug 修复和 UI 改进

## 1.8.0 (2019-08-17)

- 选择“可访问文件夹”时可同时选择多个模板及自定义
- 增加“文件夹分析”功能，获知隔离存储空间中文件夹大小
- 可访问文件夹中选择的文件夹不存在时会自动建立
- 一些些 UI 改进和 bug 修复

## 1.7.5 (2019-08-06)

- 修复“同步文件夹”功能坏掉

## 1.7.4 (2019-08-05)

- 在 Android Q 上使用 `FLAG_PERMISSION_SYSTEM_FIXED` 来固定权限
- 为华为设备提供解决方法，[详见此处](./guide/compatibility/huawei.html)
- 修复“同步文件夹”功能没有尝试处理“从目标文件夹移走文件”事件
- 改进英语翻译
- 其他小改动

## 1.7.2

- Fix "Code 5"
- Other bug fix

### 1.7.0

* Basic mode now works on Android Q beta 4
* Correctly handle hide/unhide (commonly used by "Freeze" apps)
* Change target SDK version to 29 (Android Q)

### 1.6.12

* Fix app list not refreshed after restoring backup
* Use a more reliable method to monitor app install/uninstall
* Notify user if no browser app available when opening help documents
* Fix a bug related "Fix app interaction issues" 
* Other bug fix
* UI improve

### 1.6.9

* Fix Enhanced mode not work for apps starts early than core service

### 1.6.8

* Fix apps not starting on new users
* Support Android Q beta 3 (including Enhanced mode)
* Remove the ability to choose "Android/sandbox" as isolated storage path since from Q beta 3 the system sandbox is only used for apps which declared support the sandbox

### 1.6.7

* Clear config (app info - storage - clear/manage data) feature dose clear all configs now
* Filter duplicates or incorrect mounts in the final stage to avoid problems from user misuse
* Fix "Fix app interaction issues" may incorrectly handle files in `Android/data(media, obb)/package`

### 1.6.6

* Fix app interaction issues (Enhanced mode): Grant content uri permission
* UI improve

### 1.6.4

* Fix app interaction issues (Enhanced mode): Always convert file uri to content uri on Android Q
* Enhanced mode: remove disable file uri expose check since it is meaningless
* Allow choosing "Android/sandbox" as isolated storage path on Android Q
* Other bug fix

### 1.6.3

* Enhanced mode works on Android Q
* Enhanced mode: force disable file uri expose check for Android Q system ui
* Improve App settings UI
* Try fix config lost (should be extremely rare), add "Debug info" for users to investigate this problem
* Fix storage permission can't be revoked if redirect is already disabled

### 1.6.2

* Add "View gallery as this app", you can learn which photos the app can access
* Bug fix & UI improve

### 1.6.0

* Works on Android Q DP2 (enhanced mode not supported yet)
* Change behavior, mount Android/media/xxx & Android/obb/xxx by default
* Huge UI improve
* Fix "Fix app interaction issues" never worked on some devices

### 1.5.7

* Continue fixing bugs caused by "Fix app interaction issues"
* Continue renaming options

### 1.5.6

* Fix new storage permission method breaks on MIUI
* Fix "Fix app interaction issues" feature causes app breaks on some situations (if extra contains Parcelables from non-BootClassloader)

### 1.5.5

* (Android 6.0-7.1) Fix "Fix app interaction issues" feature cause app crash or all media not shown
* Continue renaming options, app name would even change in the future
* Reduce extra app launching time
  
  On my OnePlus 3T, average extra time reduced from 0.3s to 0.16s
  
  * Enforce storage permission with API (do not need check everytime), save average 0.04s
  * (only on 7.0+) Limit "File monitor" hook target, save average 0.1s
  
### 1.5.3

* Enhancement module v19, please upgrade as soon as possible

  * "Fix app interaction issues": try bypassing the problem that apps use "Tencent app protect" (腾讯乐固) will crash (v19)
  * "Fix app interaction issues": fix some media are filtered incorrectly (app 1.5.1, v19)
  * "Fix app interaction issues": fix app may crash when "Access files from other redirected app" rules enabled (v18.1)

### 1.5.0

* New Enhancement module v18
  
  Rewrite "Fix file uri" feature, upgrade to "Fix app interaction issues" feature 
  
* UI change
* Rename some options, reduce the understanding difficulty

### 1.4.9

* Fix "Synced folders" feature is broken in 1.4.8

### 1.4.8

* Fix regex check of "Synced folders" rules is not proceed when enabling the rule
* Revoke app storage permission automatically when disabling redirect
* Other bug fix

### 1.4.7

* Fix Enhancement module installation error reporting
* Fix Google purchase issue reporting
* Bad connection with Google Play will not freeze the whole app forever (but 5s)
* Fix "Fix file uri" feature in Enhancement module may sometimes crash redirected app 
* Correctly report some type of error on start
* Other bug fix

### 1.4.6

* Improve Enhancement module installation detection and provide solution
* Improve "Invalid license" page
* Bug fix

### 1.4.4

* Bug fix

### 1.4.2

* Report Enhancement module not correctly installed
* Improve home

### 1.4.1

* Fix license check

### 1.4.0

* New home page
* Rename/re-layout options, reduce the understanding difficulty

  * "Non-redirect folders" -> "Read/writable folders in real storage"
  * "Link" -> "Synced folders"

* New Enhancement module v17, not more "I can't open redirected apps"
* Fix tons of bugs

### 1.3.3

* Fix bug of Enhance module v16

### 1.3.2

* Enhance module v16, fix a problem related to passing file uri
  (Example: can't open a received file in WeChat)
* New native starter (for some strange devices without executables like `chmod`, `rm`)
* Fix bugs related to link feature
* Other minor bug fix

### 1.2.2

* Fix mask template for link rule editor
* Add "Link function only" filter in "Logcat"
* Minor bug fix

### 1.2.1

* Add "Kill Media Storage on start" option
  (on some devices, Media Storage can use all CPU on boot, kill it can solve the problem
  (it can be started by other apps later))
* Add mask template for link rule editor
* Try to detect no log
* Minor bug fix

### 1.2.0

* Add "Shared folder" to solve the problem that files created by
  a redirected app can't be used by another redirected app
* Refreshed detail UI
* Enhanced "Redirect storage viewer"
* Enhanced filter for "File monitor"
* Enhance module v15, fix the problem that redirect apps can't move files between specific folders
  (Example: bilibili can't save gif)
* Minor bug fix

### 1.1.4

* Enhanced "Non-redirect folders" template mechanism
* Show conflicting rule info

### 1.1.2

* Simplified detail UI
* Try to support other su, confirmed support MagiskSU, SuperSU, LineageOS addonsu now
* Fix the problem that server may send wrong progress to client
  when change "Default redirect target"
* Delete redirected app config after that app uninstall
* Improve app list performance
* Improve chooser dialogs
* Improve File monitor
* Add non standard behavior check (use file monitor data)

### 1.0.2

* Fix UI not refreshed when add link rules online
* Fix the problem that "You have already own this item" happens on some Google Play users

### 1.0.0

* Add "Non-redirect folders" template, you can create different templates
  for different situations and apply them quickly
* Enhance module v14, changes behavior, may avoid some special problems on
  some devices
* Bug fix

### 1.0.0-rc9

* New logcat UI
* Fix unpaid state check
* Migrate to AndroidX library

### 1.0.0-rc8

* Improve user experience
* Minor bug fix

### 1.0.0-rc7

* Fix "Launch" button not work

### 1.0.0-rc6

* Improve user experience
* Bug fix

### 1.0.0-rc5

* Add White / Light blue theme
* Try to hide overlay packages
* Fix can't open installer in file browser
* Fix some link rules can't be added
* Bug fix

### 1.0.0-rc4

* Add manually set /data/media path for some special devices
* Bug fix

### 1.0.0-rc3

* Fix Android/data can be chosen as a "Non-redirect folder"
* Bug fix

### 1.0.0-rc1

* New theme
* New detail UI
* Add local link rule
* Multi-user support
* Fix backup bug, but backup files created before 1.0.0-rc1 is unavailable
* Try to detect real internal storage path

### 0.18.2-beta

* Fix bug

### 0.18.0-beta

* "Non-redirect folder" (old "Standard folder") is now customizable like "Redirect target folder"
* Add Backup & restore
* Works with LineageOS's addonsu, but some non-core feature may break, still recommended to use Magisk
* Fix crash when change filter in the main list
* Fix redirected files may not be moved when change redirect target folder in some cases

### 0.17.4-beta

* Fix link feature not on some (old? special?) devices
* Try to fix owner of linked files' is 0 on older Android system (chown ourselves)

### 0.17.3-beta

* Fix a critical bug that if an app's redirect target is set different
  from the default, it will not able to access files in public folders
* Fix others bugs in 0.17.x

### 0.17.1-beta

* Add set redirect target folder (globally and pre-app)
* Add app installed notification
* Also kill by uid when force stop package (for OnePlus stock ROM)
* Improved "Share helper"
* Bug fix

### 0.16.4-beta

* Add file stat for Redirect storage viewer
* Fix the problem that anyone is displayed as purchased
* Auto clean old server files
* Try to "fix" IAP problem "You have already own this item"
* Link files from target to source when enabling link rules

### 0.16.2-beta

* Enhanced File monitor: load more & filter by path / app
* Force grant storage permission for redirected apps
* Try to fix bug of link function (when create and delete files in a very short time)
* Create ".nomedia" file in Android/data/xxx automatically
* Add shortcut for File monitor (Android 7.1+)
* Fix crash when open help if no browser app installed
* Add more tips
* Fix bugs in 0.16.1 / 0.16.2

### 0.15.8-beta

* Files downloaded by redirected apps can be managed in Android's Files (DocumentUI) app
* Fix log parse (only some special ROM)
* Add "Show disabled apps" filter
* New app list style
* In-app logcat now catches logs from more sources

### 0.15.4-beta

* Fix reboot when new file created in folders monitored by link function (only on 8.0)
* Fix a bug of file monitoring function of the link function

### 0.15.2-beta

* Try to fix crash on boot (only some users)
* Fix log parse (only some special ROM)
* Auto shrink file monitor database file

### 0.15.1-beta

* Enhance module v12.1

  Fix problem that all apps unable to access the storage (only appears on some devices), but it brings some minor problems (only happens on limited situation), check Help for detail.

* Other minor changes

### 0.15.0-beta

* New Enhance module (check Settings and Help)
* File monitor: monitor file access in public storage (requires "Enhance module")
* Try to fix bugs in 0.14.3

### 0.14.3-beta

* Try to fix bugs in 0.14.1 / 0.14.2
* Magisk module v10 (check Help & support)

### 0.14.1-beta

* Provide new Magisk module to solve the problem that redirected apps still create files sometimes, check Help & support for detail
* New native daemon
* Adapt Magisk v16.4
* Improve UI
* App list will be loaded correctly now even if instant app is installed (Android 8.0's bug)

### 0.12.13-beta

* Link rule: fix the problem that some files are skipped

### 0.12.12-beta

* Fix the problem that some processes are ignored on **some special ROMs**
* Link rule: ignore file which extension ends with _tmp_ or _temp_ by default

### 0.12.11-beta

* Some bug fix

### 0.12.7-beta

* Fix the problem that some process is not redirected (from 0.12.6)
* Link rule: handle file downloaded notification by our app

### 0.12.6-beta

* Should work on Android P DP1
* Link rules ignore .tmp / .temp by default
* Some minor changes

### 0.12.5-beta

* Update Magisk module (download from Help & support)
* Some minor changes

### 0.12.4-beta

* New link rules UI
* Mark outdated (not exists in online configuration) link rules
* Try to avoid some magic
* Add "Share helper"

### 0.12.3-beta

* Add more log for starter
* More core files to /data/adb
* Try to avoid strange behavior on some devices when using Magisk module

### 0.12.1-beta
* **The core feature should works perfectly on all devices**
* Provide Magisk module for starting before all apps (see Help & support)

### 0.12.0-beta

* Fix major issue on some devices
* Add tip when log may be disabled
* Linked files will only be deleted when redirected app is running in the foreground

### 0.11.2-beta

> Version 0.11.2 changed some implementation details, to avoid some magic problems on users who have problems using version 0.11.0

* Should work on more devices now, to the user who still have problem, the problem should not break all things
* Storage permission (both runtime permission and appops) will be automatically grant to redirected apps (to avoid magic problem)

### 0.11.0-beta

> In 0.11.0 and later version, we use a completely different method of implementation. The problem that hard-coded `/sdcard` cannot be redirected is solved.
> If you have problem using the new version, please contact us for help.

* A completely different implementation, guarantee that all files will be redirected (**Read help in "Help & support" for more detail**)
* Server can be restarted without rebooting (**Reboot is required if upgrade from 0.9.x**)
* Add redirected file browser
* Add logcat
* Add detailed help
* Add "verified app" mark which means the app will never write files in non-standard dictionaries
* Remove "Block writing file" feature since it is unnecessary now
* Fix bug about link