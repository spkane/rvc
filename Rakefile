begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "rvc"
    gem.summary = "vSphere console UI"
    #gem.description = ""
    gem.email = "rlane@vmware.com"
    gem.homepage = "https://github.com/vmware/rvc"
    gem.authors = ["Rich Lane", "Christian Dickmann"]
    gem.add_dependency 'rbvmomi', '>= 1.6.0'
    gem.add_dependency 'trollop', '>= 1.16.2'
    gem.add_dependency 'backports', '>= 1.18.2'
    gem.add_dependency 'highline', '>= 1.6.1'
    gem.add_dependency 'zip', '>= 2.0.2'
    gem.add_dependency 'terminal-table', '>= 1.4.2'
    #gem.add_dependency 'ffi', '>= 1.0.7'
  end
rescue LoadError
  puts "Jeweler not available. Install it with: gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new do |t|
  t.libs << "test"
  t.test_files = FileList['test/test_*.rb']
  t.verbose = true
  t.ruby_opts << "-rubygems"
end
begin
  require "simplecov"

  desc "Measures test coverage using simplecov"
  task :simplecov do
    ENV["COVERAGE"]="true"
    Rake::Task["test"].execute
  end
rescue LoadError
  puts "simplecov not available. Install it with: gem install simplecov"
end
begin
  # HACK rvc needs to be installed as a gem
  require 'rvc'
  require 'ocra'
  desc 'Compile into a win32 executable'
  task :exe do
    sh "ocra bin/rvc"
  end
rescue LoadError
  puts "OCRA not available. Install it with: gem install ocra"
end
