# NestedHashHelper

NestedHashHelper gem's aim is to make your life easier in dealing with nested hashes . If you have been working with Rails , You must have noted that You are dealing with nested hashes ( like params from the front end) a lot . 

There are various methods added in the official Ruby code to handle nested hashes , but still it lacks lots of common and useful methods . NestedHashHelper aims to help you with those , so that you can deal with hashes easily in your application . 

Development has just begun and is active and we will fix bugs , enhance functionality of existing methods and develop new methods in the upcoming version.

## Usage

###1) deep_except(*excluded_keys)
   
  This method extends the functionality of except method of ruby hash to nested hash. pass any number of keys to delete them from the hash . Just pass the immediate key and not the entire key path in the hash . 

  Syntax 
  ```ruby  
  a = {:name => "vivek" , :age => 22}  
  a.deep_except(:name)  
  output ==> {:age => 22}  
  ```  

  ```ruby  
  a = {:user => {:name => "vivek" , :age => 22 , :phone => 3333}}  
  a.deep_except(:phone , :age)  
  output ==> {:user => {:name => "vivek"}}  
  ```  



### 2) deep_delete_empty
   
   This method deletes all the keys whose value is either empty or nil .

  Syntax   
   ```ruby  
   a =  {:user => {:name => "" , :age => 22 , :phone => 3333}}    
   a.deep_delete_empty  
   output ==> {:user => {:age => 22 , :phone => 3333}}  
   ```  


### 3) find_depth

   This method finds the depth of your nested hash.

  Syntax   
  ```ruby  
  a = {:user => {:name => {:last_name => "Vivek"}}}  
  a.find_depth  
  output ==> 3  
  ```  


### 4) find_deep_intersection

  This method returns intersection of two nested Hashes.

   Syntax   
   ```ruby  
   a = {:user => {:name => "vivek" , :age => 22 , :phone => 3333}}  
   b = {:user => {:name => "rakesh" , :age => 22 , :phone => 3333}}  
   a.find_deep_intersection(b)  
   output ==> {:user => {:age => 22 , :phone => 3333}}  
   ```  

### 5) find_deep_keys
 
  This method return all the parent keys of the corresponding value.


  Syntax 
  ```ruby
   a = {:gh => {:jj => {:pop => "bbb" , :olo => "ooooo"}} , :pp => "ooooo"}  
   a.find_deep_keys("ooooo")  
   output ==> [:gh , :jj , :olo]  
   ```

### 6) hash_to_array
      This method will convert the given nested hash to an array

      Syntax
      a =  {:fg => {:gh => {:bn => "sdjkhds"} , :jk => ""} , :kl => {:gh => "" , :jk => "sdjkhds"}}
      a.hash_to_array
      output ==> [[:fg, [:gh, [:bn, "sdjkhds"]], [:jk, ""]], [:kl, [:gh, ""], [:jk, "sdjkhds"]]]

      a = {:fg => {:gh => {:bn => ""}} , :kl =>{:jk => "nnnnnnn"}}
      a.hash_to_array
      output ==> [[:fg, [:gh, [:bn, ""]]], [:kl, [:jk, "nnnnnnn"]]]  

### 7) deep_delete(key)
    This method is used to delete a key in a nested hash
     
     Syntax
        a = {:fg => {:gh => {:bn => "sdjkhds"} , :bn => ""} , :kl => {:gh => "" , :jk => "sdjkhds"}}
        a.deep_delete(:gh)
        output ==> {:fg=>{:bn=>""}, :kl=>{:jk=>"sdjkhds"}}   

### 8) find_all_values(key)
     This method is used to find all the values of a given key 

     Syntax  
      data = {:students => {:a =>{:name => "vivek"} , :b=>{:name => "rakesh"}}}
      data.find_all_values(:name)
      output ==> ["vivek" , "rakesh"]

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'nested_hash_helper'
```

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install nested_hash_helper


## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Do Contribute if you come across any bugs / any important feature you feel is essential.

Bug reports and pull requests are welcome on GitHub at https://github.com/vivek3894/nested_hash_helper.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

