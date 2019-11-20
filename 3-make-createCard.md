You need to be in card-exercise branch
### Video 22

Card needs to be put in 2 places
 - in lists
 - in cards

State of created card need to be saved in local state of component, not in redux

### make CreateCardContainer.js

- make MapDispatchToProps
* make `defaultCardData` const obj with default values

0. Where do you get `dispatch` function from?
1. You need to create function `createCard(listId, cardData)` that needs to be
   accessible in  of `CreateCard` component, which purpose is to `dispatch`
   action obj

NOTE:
`dispatch` function needs to dispatch action object with {type: "CARD_CREATE", payload: {card, listId, cardId}}


When you hook up to use: CreateCardContainer it needs to accept listId so it can add it to lists - [HINT](CreateCardContainer needs to be in use List.js)

RESULT:
When you click on CreateCard in UI, you must be able to see action obj being dispatched with 
```
{type: "CARD_CREATE", payload: {card: {stuff}, listId: str, cardId: str}}
```

### Video 23

Card needs to be handled in list-reducer & card-reducer

1. Listen for action type "CARD_CREATE" in both list & card reducer & add it to redux store
    * [HINT 1](make sure you are returning new obj from reducers, rather then the same. Keep it pure.)
    * [HINT 2]({...cards.entities, [cardId]: card })

3. When working with normalized state you need to do what? 
   - [Answer](always add new id ot ids or result array)
4.  [HINT: List reducer ]("cards: entities[listId].cards.concat(cardId)")


RESULT: 
Your state in redux needs to have new `card` in `cards` and in `lists`, and
consequently show new card in list to user


Closing though: 

The same thing should happend for users & lists

### Video 24

## Solution For Narly code to keep imutable
lodash set helper(less complex) or Immutable.js

Regular set from lodash will mutate the object, that's why fp version

RESULT: 

Make use of:
```
import set from `lodash/fp/set
```

time: 2:03 started to use `set`


Ideas for new abstractions: 2:55
you can even crate addCartToList 

Or even better abstraction: 
addEntities or addChildIdToEntities, then create addCartToList from those
abstractions and then unit test it and never think about it again.

## Hot Tip
Take an eye for the code that makes you sad, and see can you abstract it.

### Video 25

Examples of `addEntity` & `addIdToChildren`


You need to create ACTION TYPES with in /actions dir and refactor
MapDispatchToProps by creating action creator & return the action obj, and later bind it by passing that obj to `connect`

Implement addUsers & removeCards, move cards between lists

