# Vardoc Update
General instructions on how to update Vardoc

# 1 - Read the release notes to know what had been changed.

For each stable release we will have some notes, and extra steps,
developers need to do to update the last release to the new release.


#  For Example:
* https://www.drupal.org/project/vardoc/releases/8.x-1-beta1
* https://www.drupal.org/project/vardoc/releases/8.x-1-beta2
* https://www.drupal.org/project/vardoc/releases/8.x-1-beta3
* https://www.drupal.org/project/vardoc/releases/8.x-1-0-rc1


# 2 - Backups

* Backup your project database.
* Backup your project files.
* Test restore your backups, on a test restore site.

# 3 - Get the packaged files for the new version of Vardoc 8.1.x

* From Drupal website: https://www.drupal.org/project/vardoc
* With the composer using vardoc-project: https://packagist.org/packages/vardot/vardoc-project

# 4 - From your terminal, change directory to the root directory of your
#     project to do the update:

# For Example:

```
Given that we do have a project at the /var/www/html/projects/example folder
  And we do have our custom themes, features, custom modules in
   /var/www/html/projects/example/themes/custom/
   /var/www/html/projects/example/modules/custom/
   /var/www/html/projects/example/sites/default
so on ...
like contributed modules which we had theme added
while working on the project.

  And we opened a terminal console window
  And we changed directory to our project folder
  cd /var/www/html/projects/example in Linux

  When we delete all files and folders, except our changes on Vardoc.
  Then we will be left with only custom changes

  When we copy all Vardoc files
  And we make sure that we do not have any overridden files or folders
     only delete old ones and copy new folder of modules to the same place
```

# 5 - Set the right file permissions.
# 6 - Update composer packages. use "composer outdated"
# $ composer update

  Make sure that you do have modules in the right place.

# 7 - Import Vardoc Core Features and Bundles:

```
 Given that you are logged in with the "webmaster" user
   And the "Features" module is enabled
   And the "Features UI" module is enabled
  When you go to "admin/config/development/features"
  Then you should not see any changed features in the Vardoc core bundle.
  When you click on all "Changed"
  Then you will be able to see all changes
   And you will be able to import new changes if you need them
```

# 8 - Do your Drupal 8 database updates

* By the terminal "drush updb".
* By the web browser by going to "yousite.domain/update.php"

# 9 - Regression test the full site.

* Done :\)

---


# Updating Vardot 8.1.0-beta3 to Vardot 8.1.0-rc1


## First way is by updating files with Copy and Paste for Vardot 8.1.0-rc1 over Vardoc 8.1.0-beta3
```
  Given that we are at the drupal root folder for Vardoc
   When we delete all drupal core folders and files
    And we copy all new Vardoc files drupal root folder for Vardoc
    And we make sure that we have all custom module or themes still in the
        "sites" folder
    And we make sure that all new used modules and features are present.
   Then we will be ready to update the active config and database.
```

## The composer way of Vardoc Procedures to update the base code.
   not in any vardoc-project or vardoc-project project builders.
```
  Given that we are at the root folder for Vardoc project, not the docroot
    And we make sure that the current "vardoc-project" composer.json file and
        files are the latest
   When we delete the "vendor" folder
    And we delete the "composer.lock" file
    And we run the "composer require vardot/vardoc:8.1.0-rc1" command
    And wait for composer to finish work
   Then we should not see any issues in the terminal
    And we should see "Writing lock file" in the terminal
    And we should see "Generating autoload files" in the terminal
   When the composer finishes work with no errors
   Then we will be ready to update the active config and database.
```

## Updating the active config and database from Vardot 8.1.0-beta3 to Vardot 8.1.0-rc1
```
  Given that we are in the docroot of the current Vardoc project
    And all files are updated using (copy and past) or (composer require/update
   When we run drush "updb" or go to "/update.php"
   Then we should see the steps of updates.
   When we run drush "updb" or go to "/update.php" again
   Then we will have the site update with the new Vardoc 8.1.0-rc1 version
   When we go to "/admin/config/development/features"
   Then we should see "Changed"
   When we follow with each feature to import new changes.
   Then we will have the Vardoc site updated to the latest version.
```



# Updating Vardot 8.1.0-beta2 to Vardot 8.1.0-beta3


## First way is by updating files with Copy and Paste for Vardot 8.1.0-beta3 over Vardoc 8.1.0-beta2
```
  Given that we are at the drupal root folder for Vardoc
   When we delete all drupal core folders and files
    And we copy all new Vardoc files drupal root folder for Vardoc
    And we make sure that we have all custom module or themes still in the
        "sites" folder
    And we make sure that all new used modules and features are present.
   Then we will be ready to update the active config and database.
```

## The composer way of Vardoc Procedures to update the base code.
   not in any vardoc-project or vardoc-project project builders.
```
  Given that we are at the root folder for Vardoc project, not the docroot
    And we make sure that the current "vardoc-project" composer.json file and
        files are the latest
   When we delete the "vendor" folder
    And we delete the "composer.lock" file
    And we run the "composer require vardot/vardoc:8.1.0-beta3" command
    And wait for composer to finish work
   Then we should not see any issues in the terminal
    And we should see "Writing lock file" in the terminal
    And we should see "Generating autoload files" in the terminal
   When the composer finishes work with no errors
   Then we will be ready to update the active config and database.
```

## Updating the active config and database from Vardot 8.1.0-beta2 to Vardot 8.1.0-beta3
```
  Given that we are in the docroot of the current Vardoc project
    And all files are updated using (copy and past) or (composer require/update
   When we run drush "updb" or go to "/update.php"
   Then we should see the steps of updates.
   When we run drush "updb" or go to "/update.php" again
   Then we will have the site update with the new Vardoc 8.1.0-beta3 version
   When we go to "/admin/config/development/features"
   Then we should see "Changed"
   When we follow with each feature to import new changes.
   Then we will have the Vardoc site updated to the latest version.
```

