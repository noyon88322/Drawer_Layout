# Drawer_Layout




### Part: 1

 res>xml>nav_header

   ```bash

   <?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:background="@color/orange"
    android:orientation="vertical">


    <de.hdodenhof.circleimageview.CircleImageView
        android:id="@+id/imageprofile"
        android:layout_width="@dimen/_150sdp"
        android:layout_height="@dimen/_150sdp"
        android:src="@drawable/user"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.538"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.232"
        app:civ_border_color="@color/white"
        app:civ_border_width="@dimen/_2sdp"
        android:padding="@dimen/_10sdp"
        android:layout_gravity="center"
        />
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Noyon Biswas"
        android:gravity="center"
        android:textSize="@dimen/_20ssp"
        android:padding="@dimen/_5sdp"
        android:textColor="@color/white"
        android:layout_marginBottom="@dimen/_5sdp"
        />





</LinearLayout>


   ```



  ### Part: 2

 res>menu>nav_item 

 
 
   ```bash

<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:android="http://schemas.android.com/apk/res/android">


    <group
        android:id="@+id/gp1">

        <item
            android:id="@+id/home"
            android:title="Home"
            android:icon="@drawable/home"
            android:iconTint="@color/white"
            android:checkable="true"

            />

        <item
           android:id="@+id/favourite"
            android:title="Favourate"
            android:icon="@drawable/favorite"
            android:iconTint="@color/white"
            android:checkable="true"
            />

    </group>



    <group android:id="@+id/gp2">

        <item
            android:id="@+id/share"
            android:title="Share Me"
            android:icon="@drawable/share"
            android:iconTint="@color/white"
            android:checkable="true"
            />
        <item
           android:id="@+id/rateNow"
            android:title="Rate Now"
            android:icon="@drawable/star_rate"
            android:iconTint="@color/white"
            android:checkable="true"
            />
        <item
            android:id="@+id/termcondition"
            android:title="Term And Conditions"
            android:icon="@drawable/term_condition"
            android:iconTint="@color/white"
            android:checkable="true"
            />



    </group>



</menu>


   ```


main_activity.xml

   ```bash

<?xml version="1.0" encoding="utf-8"?>
<androidx.drawerlayout.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/drawerLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    tools:openDrawer="start">

    <androidx.coordinatorlayout.widget.CoordinatorLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        
        >
       <com.google.android.material.appbar.AppBarLayout
           android:layout_width="match_parent"
           android:layout_height="wrap_content"

           >

         <com.google.android.material.appbar.MaterialToolbar
             android:id="@+id/toolBar"
             android:layout_width="match_parent"
             android:layout_height="?attr/actionBarSize"
             android:background="@color/orange"
             app:title="@string/app_name"
             app:titleTextColor="@color/white"
             app:navigationIcon="@drawable/navigation_drawer"
             app:navigationIconTint="@color/white"
             app:menu="@menu/toolbar_item"

             />

       </com.google.android.material.appbar.AppBarLayout>
        
        <FrameLayout
            android:id="@+id/frameLayout"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"

            />

        
    </androidx.coordinatorlayout.widget.CoordinatorLayout>


    <com.google.android.material.navigation.NavigationView
        android:id="@+id/navigationView"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        app:headerLayout="@layout/nav_headbar"
        app:menu="@menu/nav_item"

        />



    

</androidx.drawerlayout.widget.DrawerLayout>


   ```


## Part 3

main_activity.java
   ```bash


package com.example.status;

import android.os.Bundle;
import android.view.MenuItem;
import android.widget.FrameLayout;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.annotation.NonNull;
import androidx.appcompat.app.ActionBarDrawerToggle;
import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;
import androidx.core.graphics.Insets;
import androidx.core.view.GravityCompat;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import androidx.drawerlayout.widget.DrawerLayout;
import androidx.recyclerview.widget.RecyclerView;

import com.google.android.material.appbar.MaterialToolbar;
import com.google.android.material.navigation.NavigationView;

public class MainActivity extends AppCompatActivity {

    private DrawerLayout drawerLayout;
    private MaterialToolbar toolBar;
    private RecyclerView recycler;
    private NavigationView navigationView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        init();
        clickListener();
       




    }

    private void init() {
        drawerLayout = findViewById(R.id.drawerLayout);
        toolBar = findViewById(R.id.toolBar);
        recycler = findViewById(R.id.recycler);
        navigationView = findViewById(R.id.navigationView);


        ActionBarDrawerToggle toggle = new ActionBarDrawerToggle(
                MainActivity.this,drawerLayout,toolBar,R.string.drawer_open,R.string.drawer_close
        );
        drawerLayout.addDrawerListener(toggle);

    }

    private void clickListener(){


        navigationView.setNavigationItemSelectedListener(new NavigationView.OnNavigationItemSelectedListener() {
            @Override
            public boolean onNavigationItemSelected(@NonNull MenuItem item) {

                switch (item.getItemId()){

                    case R.id.home:
                        Toast.makeText(MainActivity.this, "Home", Toast.LENGTH_SHORT).show();
                        drawerLayout.closeDrawer(GravityCompat.START);
                        break;
                    case R.id.favourite:
                        Toast.makeText(MainActivity.this, "favourite", Toast.LENGTH_SHORT).show();
                        drawerLayout.closeDrawer(GravityCompat.START);
                        break;
                    case R.id.share:
                        Toast.makeText(MainActivity.this, "share", Toast.LENGTH_SHORT).show();
                        drawerLayout.closeDrawer(GravityCompat.START);
                        break;
                    case R.id.rateNow:
                        Toast.makeText(MainActivity.this, "rateNow", Toast.LENGTH_SHORT).show();
                        drawerLayout.closeDrawer(GravityCompat.START);
                        break;
                    case R.id.termcondition:
                        Toast.makeText(MainActivity.this, "termcondition", Toast.LENGTH_SHORT).show();
                        drawerLayout.closeDrawer(GravityCompat.START);
                        break;
                }

                return true;
            }
        });




    }


}



   ```


