# Ancestry Changelog

Doing our best at supporting [SemVer](http://semver.org/) with
a nice looking [Changelog](keepachangelog.com).

## Version [Unreleased] <small>...</small>

## Changed

* Dropping Rails 3.0 and 3.1. Added Rails 5.1 support (thx @ledermann)

## Fixes

* Performance: Use `pluck` vs `map` for ids (thx @njakobsen and @culturecode)
* Fixed acts_as_tree compatibility (thx @crazymykl)
* Fixed loading ActiveRails prematurely (thx @vovimayhem)

## Version [2.2.2] <small>2016-11-01</small>

### Changed

* Use `COALESCE` only for sorting versions greater than 5.0
* Fixed bug with explicit order clauses (introduced in 2.2.0)
* No longer load schema on `has_ancestry` load (thx @ledermann)

## Version [2.2.1] <small>2016-10-25</small>

Sorry for blip, local master got out of sync with upstream master.
Missed 2 commits (which are feature adds)

### Added
* Use like (vs ilike) for rails 5.0 (performance enhancement)
* Use `COALESCE` for sorting on pg, mysql, and sqlite vs `CASE`

## Version [2.2.0] <small>2016-10-25</small>

### Added
* Predicates for scopes: e.g.: `ancestor_of?`, `parent_of?` (thx @neglectedvalue)
* Scope `path_of`

### Changed
* `arrange` now accepts blocks (thx @mastfish)
* Performance tuning `arrange_node` (thx @fryguy)
* In orphan strategy, set `ancestry` to `nil` for no parents (thx @haslinger)
* Only updates `updated_at` when a record is changed (thx @brocktimus)
* No longer casts text primary key as an integer
* Upgrading tests for ruby versions (thx @brocktimus, @fryguy, @yui-knk)
* Fix non-default ancestry not getting used properly (thx @javiyu)

## Version [2.1.0]  <small>2014-04-16</small>
* Added arrange_serializable (thx @krishandley, @chicagogrrl)
* Add the :touch to update ancestors on save (thx @adammck)
* Change conditions into arel (thx @mlitwiniuk)
* Added children? & siblings? alias (thx @bigtunacan)
* closure_tree compatibility (thx @gzigzigzeo)
* Performance tweak (thx @mjc)
* Improvements to organization (thx @xsuchy, @ryakh)

## Version [2.0.0] <small>2013-05-17</small>
* Removed rails 2 compatibility
* Added table name to condition constructing methods (thx @aflatter)
* Fix depth_cache not being updated when moving up to ancestors (thx @scottatron)
* add alias :root? to existing is_root? (thx @divineforest)
* Add block to sort_by_ancestry (thx @Iliya)
* Add attribute query method for parent_id (thx @sj26)
* Fixed and tested for rails 4 (thx @adammck, @Nihad, @Systho, @Philippe, e.a.)
* Fixed overwriting ActiveRecord::Base.base_class (thx @Rozhnov)
* New adopt strategy (thx unknown)
* Many more improvements

## Version [1.3.0] <small>2012-05-04</small>
* Ancestry now ignores default scopes when moving or destroying nodes, ensuring tree consistency
* Changed ActiveRecord dependency to 2.3.14

## Version [1.2.5] <small>2012-03-15</small>
* Fixed warnings: "parenthesize argument(s) for future version"
* Fixed a bug in the restore_ancestry_integrity! method (thx Arthur Holstvoogd)

## Version [1.2.4] <small>2011-04-22</small>
* Prepended table names to column names in queries (thx @raelik)
* Better check to see if acts_as_tree can be overloaded (thx @jims)
* Performance inprovements (thx @kueda)

## Version [1.2.3] <small>2010-10-28</small>
* Fixed error with determining ActiveRecord version
* Added option to specify :primary_key_format (thx @rolftimmermans)

## Version [1.2.2] <small>2010-10-24</small>
* Fixed all deprecation warnings for rails 3.0.X
* Added `:report` option to `check_ancestry_integrity!`
* Changed ActiveRecord dependency to 2.2.2
* Tested and fixed for ruby 1.8.7 and 1.9.2
* Changed usage of `update_attributes` to `update_attribute` to allow ancestry column protection

## Version [1.2.0] <small>2009-11-07</small>
* Removed some duplication in has_ancestry
* Cleaned up plugin pattern according to http://yehudakatz.com/2009/11/12/better-ruby-idioms/
* Moved parts of ancestry into seperate files
* Made it possible to pass options into the arrange method
* Renamed acts_as_tree to has_ancestry
* Aliased has_ancestry as acts_as_tree if acts_as_tree is available
* Added subtree_of scope
* Updated ordered_by_ancestry scope to support Microsoft SQL Server
* Added empty hash as parameter to exists? calls for older ActiveRecord versions

## Version [1.1.4] <small>2009-11-07</small>
* Thanks to a patch from tom taylor, Ancestry now works with different primary keys

## Version [1.1.3] <small>2009-11-01</small>
* Fixed a pretty bad bug where several operations took far too many queries

## Version [1.1.2] <small>2009-10-29</small>
* Added validation for depth cache column
* Added STI support (reported broken)

## Version [1.1.1] <small>2009-10-28</small>
* Fixed some parentheses warnings that where reported
* Fixed a reported issue with arrangement
* Fixed issues with ancestors and path order on postgres
* Added ordered_by_ancestry scope (needed to fix issues)

## Version [1.1.0] <small>2009-10-22</small>
* Depth caching (and cache rebuilding)
* Depth method for nodes
* Named scopes for selecting by depth
* Relative depth options for tree navigation methods: 
    * ancestors
    * path
    * descendants
    * descendant_ids
    * subtree
    * subtree_ids
* Updated README
* Easy migration from existing plugins/gems
* acts_as_tree checks unknown options
* acts_as_tree checks that options are hash
* Added a bang (!) to the integrity functions
    * Since these functions should only be used from ./script/console and not
      from your application, this change is not considered as breaking backwards
      compatibility and the major version wasn't bumped.
* Updated install script to point to documentation
* Removed rails specific init
* Removed uninstall script

## Version 1.0.0 <small>2009-10-16</small>
* Initial version
* Tree building
* Tree navigation
* Integrity checking / restoration
* Arrangement
* Orphan strategies
* Subtree movement
* Named scopes
* Validations


[Unreleased]: https://github.com/stefankroes/ancestry/compare/v2.2.2...HEAD
[2.2.2]: https://github.com/stefankroes/ancestry/compare/v2.2.1...v2.2.2
[2.2.1]: https://github.com/stefankroes/ancestry/compare/v2.2.0...v2.2.1
[2.2.0]: https://github.com/stefankroes/ancestry/compare/v2.1.0...v2.2.0
[2.1.0]: https://github.com/stefankroes/ancestry/compare/v2.0.0...v2.1.0
[2.0.0]: https://github.com/stefankroes/ancestry/compare/v1.3.0...v2.0.0
[1.3.0]: https://github.com/stefankroes/ancestry/compare/v1.2.5...v1.3.0
[1.2.5]: https://github.com/stefankroes/ancestry/compare/v1.2.4...v1.2.5
[1.2.4]: https://github.com/stefankroes/ancestry/compare/v1.2.3...v1.2.4
[1.2.3]: https://github.com/stefankroes/ancestry/compare/v1.2.2...v1.2.3
[1.2.2]: https://github.com/stefankroes/ancestry/compare/v1.2.0...v1.2.2
[1.2.0]: https://github.com/stefankroes/ancestry/compare/v1.1.4...v1.2.0
[1.1.4]: https://github.com/stefankroes/ancestry/compare/v1.1.3...v1.1.4
[1.1.3]: https://github.com/stefankroes/ancestry/compare/v1.1.2...v1.1.3
[1.1.2]: https://github.com/stefankroes/ancestry/compare/v1.1.1...v1.1.2
[1.1.1]: https://github.com/stefankroes/ancestry/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/stefankroes/ancestry/compare/v1.0.0...v1.1.0
