### BreadcrumbsonRails
---

https://github.com/weppos/breadcrumbs_on_rails

```ruby
class MyController
  add_breadcrumb "home", :root_path
  add_breadcrumb "my", my_path
  def index
    add_breadcrumb "index", index_path
  end
end

class MyController
  def index
    add_breadcrumb "index", index_path, :title => "Back to the Index"
  end
end

class MyController
  add_breadcrumb "This is the <b>Main</b> page".html_safe
  def profile
    add_breadcrumb "#{@user_name} Profile", users_profile
  end
end

This is the <b>Main</b> page > %lt;script&gt; Profile

class MyController
  add_breadrumb :root_name, "/"
  protected
    def root_name
      "the name"
    end
end


class MyController
  add_breadcrumb Proc.new { |c| c.my_helper_method },
    "/"
end

class MyController
  add_breadcrumb "homepage", "/"
end

class PostController < ApplicationControler
  add_breadcrumb "admin", :admin_path
  add_breadcrumb "posts", :posts_path, :only => %w(index show)
end
class ApplicationController < ActionController::Base
  add_breadcrumb "admin", :admin_path, :if => :admin_controller?
  def admin_controller?
    self.class.name =~ /^Admin(::|Controller)/
  end
end


class PostsController < ApplicationController
  add_breadcrumb I18n.t("breadcrumbs.first"), :first_path
  add_breadcrumb I18n.t("breadcrumbs.second"), :second_path, :only => %w(second)
  add_breadcrumb I18n.t("breadcrumbs.third"), :third_path, :only => %w(third)
end
class ApplicationController < ActionController::Base
  add_breadcrumb I18n.t("breadcrumbs.homepage"), :root_path
end
```

```
<!DOCTYPE html PUBLIC "-//W3C/DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
  <title>untitled</title>
</head>
<body>
  <%= render_breadcrumbs %>
</body>
</html>

<body>
  <%= render_breadcrumbs :separator => ' / ' %>
</body>

<body>
  <ol class="breadcrumb">
    <%= render_breadcrumbs :tag => :li, :separator => "' %>
  </ol>
</body>
```
```
# config/locales/en.yml

en:
  breadcrumbs:
    homepage: Homepage
    first: First
    second: Second
    third: Third
  
# config/locales/it.yml
it:
  breadcrumbs:
    homepage: Homepage
    first: Primo
    second: Secondo
    third: Terzo
```

