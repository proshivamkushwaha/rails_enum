# rails_enum

**before migration create a schema and set default:0**
```
class CreatePosts < ActiveRecord::Migration[6.1]
  def change
    create_table :posts do |t|
      t.string :title
      t.text :body
      t.integer :status, default:0

      t.timestamps
    end
  end
end
```
**then migrate and add array values to your model file**
```
class Post < ApplicationRecord
	enum status: ["Working", "Completed", "In Progress"]
end
```
**On your HTMl form show dropdown**
```
<div class="field">
    <%= form.label :status %>
    <%= form.select :status, Post.statuses.keys %>
  </div>
```

