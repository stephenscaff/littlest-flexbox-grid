# The Littlest Grid System via Flexbox

A little demo for a stupid simple and tiny grid system using a flexbox mixin.

Article on the [Pigeon Wisdom Blog ]( http://urbaninfluence.com/2016/08/a-flexy-little-grid-system/)

[Demo](http://urbaninfluence.com/demos/littlest-grid-system/)

## Project Setup

This project uses CodeKit for compiling and linting, but you can run it through your task manager of choice.

### SRC Folder

Work is done and the src folder, with scss and js compiling out their counterparts within the assets folder.

### SCSS

The SCSS folder inside src contains all related SCSS partials, with demo related styles contained in the _demo.scss folder, and The Flexbox Grid styles located in _flex-grid.scss.


Note that we're not minifing css for the sake of the demo.

## The Mixin

The mixin itself takes 5 arguments - The first 4 relate to the number of columns across 4 breakpoints (sm, med, lg, xl), and the last applies column padding. The arguments are optional, so you can add just what you need without generating any extra output. As you can see, we're using the universal selector to you can apply the grid to any parent, without having to alter your column classes - ideal for BEM syntax.


```
//----------------------------------------------  
//  flex-grid();
//  Creates grid blocks via flexbox

//  @param: $sm, $med, $lg, $xl - @media sizes
//  @param: $pad  - item padding  
//  @useage: @include g-blocks(1, 2, 3, 4, 1%);

//  @note: Can replace universal selector with '& > #{$item}''  ($item:'article')
//----------------------------------------------
@mixin flex-grid($sm:null, $med:null, $lg:null, $xl:null, $pad:0) {
  display: flex;
  flex-direction: row;
  flex-flow: wrap;
  margin-left: -$pad;
  margin-right: -$pad;
  list-style: none;

  & > * {
    padding:$pad;
    flex-basis: 100%/$sm;
    max-width: 100%/$sm;
    
    @media(min-width: $mq-med){
      flex-basis: 100%/$med;
      max-width: 100%/$med;
    }

    @if $lg {
      @media(min-width: $mq-large){
        flex-basis: 100%/$lg;
        max-width: 100%/$lg;
      }
    }

    @if $xl {
      @media(min-width: $mq-xlarge){
        flex-basis: 100%/$xl;
        max-width: 100%/$xl;
      }
    }
  }
}

//----------------------------------------------  
//  Media Queries
//----------------------------------------------
$mq-small: 32em;
$mq-med: 54em;
$mq-large: 65em;
$mq-xlarge: 91em;

```

## Useage

```
// 2 cols sm, 3 at med, 4 at lg, 0.5em of padding:
.blocks{
  @include g-blocks(2, 3, 4, $pad:0.5em);
}

// 2 cols sm, 4 at med, 1em of padding:
.blocks{
  @include g-blocks(2, 4, $pad:1em);
}

etc.
```

## License

Integrate or build upon it for free in your personal or commercial projects. Don't republish, redistribute or sell "as-is". 


## Misc

Created by Stephen Scaff: 
- [Twitter](http://www.twitter.com/stephenscaff), 
- [GitHub](https://github.com/stephenscaff), 

At Urban Influence:
- [Twitter](http://www.twitter.com/pigeonwisdom), 
- [GitHub](https://github.com/urbaninfluence)

