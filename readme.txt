=== Plugin Name ===
Contributors: blobfolio
Donate link: http://www.blobfolio.com/donate.html
Tags: security, scanner, vulnerabilities, files, validation, auditor, validator, looksee, checker
Requires at least: 3.6
Tested up to: 4.2.4
Stable tag: trunk
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Verify the integrity of a WP installation by scanning for unexpected or modified files.

== Description ==

Look-see Security Scanner is a relatively quick and painless way to locate the sorts of file irregularities that turn up when a site is hacked.  This is broken down into multiple searches:

  * Verify the integrity of all core WordPress files;
  * Search wp-admin/ and wp-includes/ for unexpected files;
  * Search wp-content/uploads/ for hidden PHP scripts;
  * Identify file changes since previous scan;
  * Locate files left over from older versions (3.6+) of WordPress;
  * Analyze configurations for oversights and vulnerabilities;
  * Check uploaded themes and plugins against the WPScan Vulnerabilities Database;
  * Search files for functions commonly used by malware;

== Installation ==

1. Unzip the archive and upload the entire `look-see` directory to your `/wp-content/plugins/` directory.
2. Activate the plugin through the 'Plugins' menu in WordPress.
3. Find 'Look-See Security Scanner' in the 'Tools' menu to run a search.

== Frequently Asked Questions ==

= Is this plugin compatible with WPMU? =

The plugin is only meant to be used with single-site WordPress installations.  Some features may still work under multi-site environments, however it would be safer to use some other plugin that is specifically marked WPMU-compatible instead.

= Does Look-See correct any problems it finds? =

No, Look-See merely points out any irregularities it finds.  It is left to you to manually review any affected files to determine whether or not they pose a threat.

= Is there anything I can do to keep my server from modifying files as I upload them? That is annoying! =

Take a look at your FTP program's settings and change the transfer type from ASCII (or automatic) to Binary.  If your program doesn't support this, try FileZilla: http://filezilla-project.org/.

= If there are no warnings, does that mean I am A-OK? =

Not necessarily. There could still be backdoors elsewhere on the server. As always, we recommend you maintain best security practices and keep regular back-ups.

= Is there a faster way to run the content analysis? My server is too slow! =

If you have command line access to your server, a command like the following will return a list of files containing various "blacklisted" functions.  (Just update the path at the end.)

`grep -E -r "\b(fsockopen|pfsockopen|proc_open|curl|exec|shell_exec|eval|hex2bin|base64_decode|passthru|unserialize|pcntl_alarm|pcntl_fork|pcntl_waitpid|pcntl_wait|pcntl_wifexited|pcntl_wifstopped|pcntl_wifsignaled|pcntl_wexitstatus|pcntl_wtermsig|pcntl_wstopsig|pcntl_signal|pcntl_signal_dispatch|pcntl_get_last_error|pcntl_strerror|pcntl_sigprocmask|pcntl_sigwaitinfo|pcntl_sigtimedwait|pcntl_exec|pcntl_getpriority|pcntl_setpriority)\s*\(" --include "*.php" /path/to/wp-content/`

Remember, these functions do have perfectly legitimate uses, so most of the results will probably be innocent.  Still, it won't hurt to take a look.

= Can scans be automated? =

Not yet, sorry.  Automated scans will probably be integrated into a future release, so stay tuned!

== Screenshots ==

1. Realtime scan progress.
2. Easy to understand scan results with expandable details and test explanations.
3. Check configuration for oversights or vulnerabilities.

== Changelog ==

= 15.08 =
* Search files for common malware functions;

= 15.03-2 =
* Improve compatibility with InnoDB installations;

= 15.03 =
* Check for existence of MySQL table before prompting to install checksums;

= 15.02-2 =
* Small db change;

= 15.02 =
* UX improvements;
* Code clean up;

= 14.12-2 =
* Look-See now gets its checksums directly from WordPress, so version support is more or less automatic and includes locale support;

= 14.12 =
* Check plugins and themes against WPScan Vulnerability Database;

= 14.11 =
* Checksums for WP 4.0.1;

= 14.09 =
* Checksums for WP 4.0;
* Removed support for 3.7.* and 3.8.*;

= 14.08 =
* Checksums for WP 3.9.2;

= 14.05.2 =
* Checksums for WP 3.7.2 and 3.7.3;

= 14.05 =
* Checksums for WP 3.9.1;

= 14.04.4 =
* Checksums for WP 3.9;

= 14.04.3 =
* Checksums for WP 3.8.3;

= 14.04 =
* Checksums for WP 3.8.2;

= 14.01 =
* Checksums for WP 3.8.1;

= 13.12 =
* Checksums for WP 3.8;

= 13.11 =
* Faster database I/O during scans (~2x faster);
* Option to ignore WP cache files;
* Updated SSL session analysis;

= 13.10.3 =
* Checksums for WP 3.7.1;
* Dropped compatibility with WordPress 3.5.*;

= 13.10.2 =
* Checksums for WP 3.7;

= 13.10 =
* Added option to scan only core files;

= 13.09.3 =
* Minor branding update;

= 13.09.2 =
* Updated list of old core files, so scan results categorize them as such rather than "suspicious";

= 13.09 =
* Checksums for WP 3.6.1;

= 13.08.3 =
* Fixed undefined variable PHP Notice;
* Fixed hang in Firefox upon scan completion;

= 13.08.2 =
* Replace deprecated $wpdb->escape() with esc_sql().

= 13.08 =
* Checksums for WP 3.6;

= 13.07 =
* Checksums for WP 3.5.2;
* Removed compatibility with WordPress 3.4.2;

= 13.05 =
* Minor update, replacing a couple functions that are deprecated as of PHP 5.5.0.

= 13.04 =
* Added support for InnoDB database engine;
* Minor speed improvements;

= 13.01 =
* Checksums for WP 3.5.1;
* Changed version naming scheme to YY.MM;

= 3.5-6 =
* Uninstallation now removes all plugin data/settings;
* Prevent installation on WPMU blogs;
* Use $_SERVER instead of getenv() as it is compatible with more environments;
* New Feature: Configuration Analysis checks for inactive themes and plugins;

= 3.5-5 =
* Bug fix: Missing files incorrectly shown as being skipped;
* New Feature: Configuration Analysis checks for phpinfo.php, SSL, WP plugin/theme editor;
* Code clean up: replaced spaces with tabs;

= 3.5-4 =
* Files left over from old WP installations are better explained in results;
* New Feature: Configuration Analysis looks for oversights and vulnerabilities in configuration;
* Bug fix: renamed duplicate form field IDs;

= 3.5-3 =
* New Setting: ignore files above a certain size;
* Ability to abort scan in progress;
* Ability to re-install WordPress core definitions;
* Various performance improvements;
* Better error handling;

= 3.5-2 =
* Fixed a potential file name bug;
* Code clean up: all queries now run through $wpdb

= 3.5 =
* Checksums for WP 3.5;

= 3.4.2-7 =
* Bug fix: case-insensitive indexes could prevent scanning all files;
* File system scanning now roughly 27% faster;
* Added set_time_limit() to help prevent execution timeouts;

= 3.4.2-6 =
* Dramatically simplified scan process and reporting;
* Queue-based scanning to improve support with slow servers;
* MD5 checksums are once again used for validating custom content;

= 3.4.2-5 =
* Switched from MD5 to CRC32 checksums for the custom file database as the former was simply too slow for many users.

= 3.4.2-4 =
* Disable automatic building of custom file database when missing; operation can take a long time on slow servers.

= 3.4.2-3 =
* Automatically build custom file database when missing;

= 3.4.2-2 =
* Fixed a bug affecting wp-content/uploads scan when uploads are split into multiple folders;
* Added custom content scan;
* Scans now report duration spent in execution;
* Improved support for Windows servers;
* Last-run timestamp for each scan;

= 3.4.2 =
* Look-See is born!

== Upgrade Notice ==

= 15.08 =
Ability to search files for common malware functions.

= 15.03-2 =
Improve compatibility with InnoDB installations.

= 15.03 =
Check for existence of MySQL table before prompting to install checksums.

= 15.02-2 =
Small db change.

= 15.02 =
UX improvements and code clean up.

= 14.12-2 =
Look-See now gets its checksums directly from WordPress, so version support is more or less automatic and includes locale support.

= 14.12 =
Check plugins and themes against WPScan Vulnerability Database.

= 14.11 =
Checksums for WP 4.0.1.

= 14.09 =
Checksums for WP 4.0. New minimum supported version is WP 3.9.

= 14.08 =
Checksums for WP 3.9.2.

= 14.05.2 =
Checksums for WP 3.7.2 and 3.7.3.

= 14.05 =
Checksums for WP 3.9.1.

= 14.04.4 =
Checksums for WP 3.9.

= 14.04.3 =
Checksums for WP 3.8.3.

= 14.04 =
Checksums for WP 3.8.2.

= 14.01 =
Checksums for WP 3.8.1.

= 13.12 =
Checksums for WP 3.8.

= 13.11 =
Scan optimizations, and updated language on Analysis page.

= 13.10.3 =
Checksums for WP 3.7.1.

= 13.10.2 =
Checksums for WP 3.7.

= 13.10 =
Added option to scan only core files.

= 13.09.3 =
Minor branding update.

= 13.09.2 =
Updated list of old core files, so scan results categorize them as such rather than "suspicious".

= 13.09 =
Added support for WordPress 3.6.1.

= 13.08.3 =
This release contains bug fixes. Firefox users are particularly encouraged to upgrade.

= 13.08 =
Added support for WordPress 3.6.

= 13.07 =
Added support for WordPress 3.5.2 and dropped support for 3.4.2.

= 13.05 =
Minor update, replacing a couple functions that are deprecated as of PHP 5.5.0.

= 13.04 =
Added compatibility for InnoDB.  NOTE: upgrading will erase currently stored scan info so you are encouraged to scan once before upgrading (to make sure nothing's out of the ordinary), and again afterward (to generate something to compare against next time).

= 13.01 =
Checksums for WP 3.5.1.

= 3.5-6 =
New features and bug fixes.

= 3.5-5 =
This release fixes a bug and provides several new analysis checks.

= 3.5-4 =
This release adds new features: configuration analysis and old core file identification.

= 3.5-3 =
This release adds new features and performance improvements.

= 3.5-2 =
This release contains a potential bug fix and code clean up.

= 3.5 =
Checksums for WP 3.5!

= 3.4.2-7 =
Fixed file name case-insensitivity issue and improved performance; it is recommended all users update.

= 3.4.2-6 =
Scan process and reporting has been dramatically simplified; additionally, support for slower servers has been greatly improved.

= 3.4.2-5 =
This release speeds up custom file scans; if your current setup is too slow, try upgrading.

= 3.4.2-4 =
This release roles back the changes of 3.4.2-3, as it proved too difficult for slow servers.

= 3.4.2-3 =
This release addresses a small bug introducedin 3.4.2-2.

= 3.4.2-2 =
This release fixes a bug affecting the wp-content/uploads scan, and also adds a new custom scan. Everyone should upgrade.
